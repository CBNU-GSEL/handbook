---
icon: lucide/play
---

# Submit an experiment

Develop and check code in your personal Coder workspace. Submit experiments
to the **`gsel-compute` Gateway** for execution.

Use the private member guide for the Gateway address and authenticated
client setup. The operations below describe the Gateway API; use the client
instructions provided for your service.

## Prepare the request

1. [Set up the project with Pixi](../projects/pixi.md), run its local checks,
   and push the revision you want to execute.
2. Read `GET /capabilities` for available projects, tasks, resource choices,
   and task parameters.
3. Select your registered project and task. Record its repository URL and
   full Git commit ID.
4. Fill in the experiment details and resource request below.

| Field | What to provide |
| --- | --- |
| `project` | Registered project name, such as `forest-change`. |
| `experiment` | A descriptive name for this experiment, such as `baseline-check`. |
| `summary` | A nonempty summary of at most 100 characters, such as "Check baseline accuracy on the validation sample." |
| `repository` | The GitHub repository URL registered for the project. |
| `commit` | The full 40-character Git commit ID for the pushed revision. |
| `task` | A task registered for the project. |
| `overrides` | Supported task parameters; use an empty list when none are needed. |
| `expected_runtime_minutes` | Estimated execution time in whole minutes, greater than zero. |
| `run_mode` | `standard` or `smoke`. |

Project and experiment names follow the
[lowercase-dash naming rules](../projects/pixi.md#project-names). Write the
summary so another researcher can understand the run's purpose.

## Request resources

Choose CPU threads and RAM from the values returned by Gateway. Select
resources for the experiment, independently of your Coder workspace size.

| Resource field | Meaning |
| --- | --- |
| `resources.cpu_threads` | Requested CPU parallelism. Match program workers and numerical-library threads to the request. |
| `resources.memory_gib` | System RAM needed for the program, data, and working buffers, in GiB. This is separate from GPU memory. |
| `resources.gpu` | Whether the experiment requires a GPU. Use `false` for CPU-only work. |
| `resources.gpu_vram_gib` | Required GPU memory in GiB. Supply a positive value only when requesting a GPU. |

Estimate peak memory use, including batches and intermediate results. A VRAM
request describes memory needed for the workload; it does not select a GPU
model. Choose values supported by Gateway and revise them after small tests.

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

## Submit and check state

1. Submit the prepared request with `POST /runs`, using the authenticated
   client and retry instructions from the member guide.
2. Save the returned `run_id`. Acceptance alone does not confirm execution;
   check `execution_enabled` and the returned state. If execution is
   unavailable, contact support before resubmitting.
3. Read `GET /runs/{run_id}` to check your run. Replace `{run_id}` with the
   returned identifier.
4. Read `GET /runs/{run_id}/logs` for its available log output.
5. After completion, check the experiment's outputs as well as its state.

| State | Meaning and next action |
| --- | --- |
| `pending` | Waiting to start. Check again later. |
| `running` | Executing. Monitor progress and logs. |
| `succeeded` | Execution completed successfully. Validate the results. |
| `failed` | Execution failed. Inspect the error before submitting a corrected run. |
| `deadline-exceeded` | The run reached its time limit. Reduce or split the workload before retrying. |
| `cancelling` | Cancellation is in progress. Check again until it finishes. |
| `cancelled` | Cancellation completed. |
| `unknown` or `missing` | The outcome cannot be confirmed. Contact support with the run ID before retrying. |
| `abandoned` | The accepted run did not execute. Contact support before retrying. |

Cancel unwanted work with `POST /runs/{run_id}/cancel`, then check its state.
If a submission times out, retain its request details and any returned run ID;
avoid sending repeated submissions while its outcome is uncertain.

For help, send the run ID, time, and a redacted error through the internal
support channel. Follow the [compute-use rules](rules.md).
