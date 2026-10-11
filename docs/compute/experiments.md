---
icon: lucide/play
---

# Submit an experiment

Develop and check code in your personal Coder workspace. Submit experiments
to the **`gsel-compute` Gateway** for execution with the `gsel-compute`
command, which the workspace provides.

Use **Submit a Gateway CPU smoke run from Coder**, the private member guide
in the infrastructure repository, for the access, cancellation, and retry
procedures. Ask your onboarding contact for access to that guide.

## Commands

Run these commands in a workspace terminal. A command that needs Gateway
access prompts you to approve a sign-in with your own GSEL account.

| Command | Purpose |
| --- | --- |
| `gsel-compute capabilities` | Print the projects, tasks, and resource choices Gateway accepts. |
| `gsel-compute submit REQUEST.json` | Submit a request file. Without a file, build the request by answering prompts from the Git checkout in the current directory. |
| `gsel-compute status RUN_ID` | Print the run's state. |
| `gsel-compute logs RUN_ID` | Print the run's state and its most recent log lines. |
| `gsel-compute smoke --commit COMMIT` | Submit the CPU smoke run and verify its result. |

An interactive submission refuses a checkout with uncommitted changes and does
not snapshot them.

## Prepare the request

1. [Set up the project with Pixi](../projects/pixi.md), run its local checks,
   and push the revision you want to execute.
2. Run `gsel-compute capabilities` to see available projects, tasks,
   resource choices, and task parameters.
3. Select your registered project and task. Record its repository URL and
   full Git commit ID.
4. Write a JSON request file with the fields below.

| Field | What to provide |
| --- | --- |
| `schema` | `gsel.run/SubmissionRequest@0.2`. Include it: `gsel-compute` sends a request file unchanged, and Gateway rejects any other value. |
| `project` | Registered project name, such as `forest-change`. |
| `experiment` | A descriptive name for this experiment, such as `baseline-check`. |
| `summary` | A nonempty summary of at most 100 characters, such as "Check baseline accuracy on the validation sample." |
| `repository` | The registered repository URL in the form `https://github.com/<owner>/<repository>`, without a `.git` suffix. |
| `commit` | The full 40-character lowercase hexadecimal Git commit ID for the pushed revision. |
| `task` | A task registered for the project. |
| `resources` | An object with the fields in [Request resources](#request-resources). |
| `overrides` | A list of supported task parameters, each written as `name=value`; use an empty list when none are needed. |
| `expected_runtime_minutes` | Estimated execution time in whole minutes, greater than zero and at most the maximum that `gsel-compute capabilities` reports. |
| `run_mode` | `standard` or `smoke`. |

Provide every other field as well; Gateway rejects a request that omits one.
Gateway also rejects any field not listed here, because it decides the image,
placement, and environment itself.

Project and experiment names follow the
[lowercase-dash naming rules](../projects/pixi.md#project-names). Write the
summary so another user can understand the run's purpose.

## Request resources

Choose CPU threads and RAM from the values returned by Gateway. Select
resources for the experiment, independently of your Coder workspace size.

| Resource field | Meaning |
| --- | --- |
| `resources.cpu_threads` | Requested CPU parallelism. Match program workers and numerical-library threads to the request. |
| `resources.memory_gib` | System RAM needed for the program, data, and working buffers, in GiB. This is separate from GPU memory. |
| `resources.gpu` | Whether the experiment requires a GPU: `true` or `false`. Use `false` for CPU-only work. |
| `resources.gpu_vram_gib` | Required GPU memory in GiB. Supply a positive value when `resources.gpu` is `true`. Omit it when `resources.gpu` is `false`; Gateway rejects it. |

Estimate peak memory use, including batches and intermediate results. A VRAM
request describes memory needed for the workload; it does not select a GPU
model. Choose values supported by Gateway and revise them after small tests.

This example shows a complete CPU-only request. Replace every value with one
from your project and from `gsel-compute capabilities`:

```json
{
  "schema": "gsel.run/SubmissionRequest@0.2",
  "project": "forest-change",
  "experiment": "baseline-check",
  "summary": "Check baseline accuracy on the validation sample.",
  "repository": "https://github.com/<owner>/<repository>",
  "commit": "<full 40-character commit ID>",
  "task": "<registered task>",
  "resources": {
    "cpu_threads": 2,
    "memory_gib": 4,
    "gpu": false
  },
  "overrides": [],
  "expected_runtime_minutes": 10,
  "run_mode": "standard"
}
```

## Runtime and run mode

Expected runtime estimates execution time after the run starts, excluding
waiting time. It does not reserve resources or extend the run's time limit.
If the run exceeds the estimate, inspect its progress and use a better
estimate for later submissions.

- **`smoke`** runs a short execution check with a shorter time limit. Choose
  a small input or reduced workload through supported task parameters. The
  mode alone does not reduce the dataset or training steps.
- **`standard`** runs the intended experiment within the service's ordinary
  time limit. Use it after the smoke run produces the expected result.

A smoke run executes code. A dry run only validates a request and does not
execute the experiment.

## Submit and check status

1. Run `gsel-compute submit REQUEST.json` with the prepared request.
2. Save the printed `request_key` and `run_id`.
3. Run `gsel-compute status RUN_ID` until the run reaches a final state.
   Use `gsel-compute logs RUN_ID` to read its recent output.
4. Check the experiment's outputs after successful completion.

| State | Next action |
| --- | --- |
| `pending` | Check again later. |
| `running` | Check status while the run executes. |
| `succeeded` | Validate the results. |
| `failed` | Inspect the reported error before submitting a corrected run. |
| `deadline-exceeded` | Reduce or split the workload. |
| `cancelling` | Check until cancellation finishes. |
| `cancelled` | No further action is needed. |
| `unknown`, `missing`, or `abandoned` | Contact support with the run ID before resubmitting. |

Use the member guide's cancellation procedure to stop unwanted work.
For an expired sign-in or a submission error, follow its recovery instructions.
Retain the request key and any run ID while the outcome is uncertain, and do
not resubmit with a new key.

## Smoke checks

Both smoke tasks belong to the `gsel-compute-demo` project.

- **CPU smoke (`cpu_smoke`)** is accepted. A run from a Coder workspace at
  source commit `e6caaaeb2011ee927669d6e90e6c59912cb66628` succeeded, and its
  source, checksum, CPU quota, and memory limit matched the request. Run
  `gsel-compute smoke --commit e6caaaeb2011ee927669d6e90e6c59912cb66628`
  to repeat that check.
- **GPU smoke (`gpu_smoke`)** has one successful run. A run at source commit
  `e6caaaeb2011ee927669d6e90e6c59912cb66628` succeeded on October 11, 2026
  (UTC). Its result allocated 4096 bytes through CUDA, and the CUDA and NVML
  device identities matched. To submit this task, set `resources.gpu` to
  `true` and provide `resources.gpu_vram_gib`. This one run does not show GPU
  performance, production readiness, or capacity for concurrent GPU runs.

For help, send the run ID, time, and a redacted error through the internal
support channel. Follow the [compute-use rules](rules.md).
