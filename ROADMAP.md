# Handbook roadmap (draft v4, 2026-10-29)

handbook을 넓히는 계획의 초안이다. 2절의 결정이 끝나면 milestone과 issue로 옮긴다. label, milestone, Project는 아직 만들지 않았다.
근거 자료는 별도 조사 보고서에 있고, 이 repo에는 아직 올리지 않았다.

## 1. 정해진 것

| 항목 | 결정 |
|---|---|
| 목적 | 연구실 구성원이 computer 활용 자료를 한 곳에서 쉽게 찾는 참고서. 백과사전도, 교육 과정도 아니다. |
| 독자 | 배경지식이 없는 신입부터 기존 연구실원까지. 운영자용 지식은 public handbook에 두지 않는다. |
| 범위 규칙 | 연구실의 결정 하나 또는 증상 하나에 연결되는 내용만 직접 쓴다. 나머지는 외부 자료 link. |
| 언어 | 영어와 한국어 둘 다. 한국어 본문에서도 전문용어는 번역·음차 없이 원어(`commit`, `Pod`, `container`). |
| 원본 언어 | 한국어. 한국어 페이지를 먼저 쓰고, 영어 페이지는 번역이다. 영어 페이지 front matter에 번역 기준이 된 한국어 commit(`source_commit`)을 적는다. |
| 한국어 문체 | 평어체(~한다)로 통일한다. 단계 설명도 "실행한다"로 쓴다. |
| License | 문서 내용은 CC BY 4.0. 문서 속 명령과 code 예제, Manim scene·mockup source는 MIT. |
| 메뉴 "Guides" | Research practices, ML/DL, Geospatial & remote sensing을 하위에 둔다. |
| 작성 원칙 | 배경지식 없이 이해되게 쓴다. 비유를 쓰지 않는다. 수사·현학 표현을 쓰지 않는다. 문장과 문단을 짧게 유지해 읽기 부담을 관리한다. 공개된 표준과 style guide를 따른다. |
| 출처 | 제품·장비·software 설명은 공식 문서를 근거로 한다. 이미지는 license가 허용할 때만 복사한다. |
| 시각화 | 개념 설명은 Manim, 구조와 흐름은 Mermaid, 사용 흐름은 HTML mockup. 글이 원본이고 그림은 보조다. |
| 실제 동작 공개 | 하지 않는다. mockup은 실제 명령 문법에 정제한 출력을 쓰고, 내부 값은 `<placeholder>`로 둔다. |
| 렌더 위치 | 공개 영상은 handbook GitHub Actions에서 render하고 Pages로 배포한다. 내부 영상은 운영자용 private repo에서 local render한다. |
| 공개 범위 | handbook repo는 public이다. issue, PR 본문, 영상 source까지 공개된다. 기준은 연구실 public publication policy다(운영자가 관리하는 private 문서). |
| 이름 | "GSEL"은 연구실 이름이다. 메뉴나 기능 이름에 쓰지 않는다. |
| AI agent | Claude Code / Codex 섹션은 계획만 한다. 연구 data를 외부 service로 보내는 것에 대한 연구실 정책이 먼저다. |
| 질문 순환 | 같은 질문이 두 번 나오면 문서로 만든다. |

## 2. 더 정할 것

추천안을 함께 적었다. 정해지면 1절로 옮긴다.

| # | 정할 것 | 추천 | 이유 |
|---|---|---|---|
| D2 | 기계 번역 허용 여부 | 허용하되 사람이 검토한 뒤 공개한다. 검토 전 페이지는 내지 않는다 | Kubernetes, Turing Way 모두 사람 검토를 요구한다. |
| D5 | issue·PR·commit 언어 | 제목과 commit은 영어, 본문과 review comment는 한국어 허용 | 기존 repo 관례와 맞고 검색이 쉽다. |
| D6 | GitHub Project 공개 여부 | private | private Project에 public handbook issue와 private repo issue를 함께 넣을 수 있다. |
| D7 | site 이름 | 지금은 "GSEL Handbook"(`zensical.toml`). "GSEL Computation Cluster Handbook"으로 바꿀지 | 제목이 다루는 범위를 정한다. |
| D9 | 영어판 공개 시점 | 최소 집합(home, Getting started, 첫 실험 제출, Troubleshooting 목록, glossary)이 번역된 뒤 언어 선택기를 연다 | 반쯤 번역된 site는 오히려 혼란을 준다(Kubernetes, PEP 545). |
| D10 | page owner와 검토 주기 | 메뉴별 owner(CODEOWNERS), 학기마다 `last_reviewed`가 오래된 페이지 검토 | 졸업 후 갱신이 멈춘 lab handbook 사례가 많다. |
| D11 | 공개 문서에 쓸지 정할 내부 사실 | workspace의 sudo 허용 여부, 일반 사용자에게 VPN이 필요한지 | publication policy 판단이 필요하다. |
| D12 | persona | 3–4개: 처음 온 신입, Python을 아는 연구원, GPU를 많이 쓰는 ML 연구원, 공간정보·원격탐사 연구원 | 페이지마다 대상 독자를 적는 기준이 된다. |
| D13 | 기존 영어 페이지 처리 | 지금 handbook 페이지는 영어로 쓰여 있다. M0에서 한국어 원본을 새로 쓰고, 영어 페이지는 번역으로 다시 표시한다 | 원본 언어를 하나로 맞춰야 낡은 번역 검사가 동작한다. |
| D14 | 기본 URL | 한국어를 site root(`/`), 영어를 `/en/`에 둔다 | 원본 언어가 기본 경로에 있어야 link가 안정적이다. |

## 3. 정보 구조

### 메뉴

| 메뉴 | 독자가 하러 온 일 | 내용 |
|---|---|---|
| Getting started | 처음 왔다 | 계정, 로그인, 첫 workspace, 첫 실험 제출, 첫 주 checklist, 질문하는 법 |
| Compute resources | 연구실 계산 자원을 쓴다 | workspace, 환경 만들기, 실험 제출, 자원 요청값 정하기, 실행 경로와 상태, 결과와 log, data와 storage 사용 규칙 |
| Concepts | 원리를 알고 싶다 | Computer & performance, Operating systems, Network, Infrastructure, Software development |
| Tools | 도구 사용법을 알고 싶다 | shell, Git과 GitHub, Pixi, Hydra, container, editor, (나중에) AI agent |
| Guides | 연구 작업을 한다 | Research practices, ML/DL, Geospatial & remote sensing |
| Troubleshooting | 지금 막혔다 | 증상과 실제 오류 문구를 제목으로 한 페이지 |
| Reference | 정확한 값을 확인한다 | glossary, 명령 요약표, 설정 field, 추천 외부 자료 |
| About | 기여하거나 규칙을 확인한다 | 기여 방법, 작성 기준, 이미지·license 정책, 번역 상태, 다루지 않는 것 |

규칙:

- 같은 설명을 두 곳에 쓰지 않는다. 도구의 일반 사용법은 Tools에, 연구실에서만 해당하는 내용은 Compute resources에 쓰고 서로 link한다.
- 각 메뉴 안에서 고급 내용은 한 단계만 숨긴다(접는 section 또는 Advanced 묶음).
- 주제(`gpu`, `storage`, `pixi` …)는 page tag로 가로지른다.
- slug는 M0에서 고정하고, 옮기면 redirect를 남긴다.

### 페이지 유형

| `type` | 첫 줄 | 본문 순서 |
|---|---|---|
| `tutorial` | 끝나면 무엇을 할 수 있는가 | 번호 단계, 단계마다 기대 출력 |
| `task` | "X를 하려면" | 선행 조건 → 단계 → 확인 방법 → 흔한 문제 → 관련 페이지 |
| `reference` | 무엇의 목록인가 | 표. 설명은 concept 페이지로 link |
| `concept` | 한 줄 정의 | 정의 → 관찰 가능한 값 → 그림 → 연구실에서는 → 관련 증상·결정 → 더 읽기 |
| `symptom` | 오류 문구 그대로 | 뜻 → 확인할 것 → 해결 단계 → 원인(concept link) → 언제 질문할지 |
| `decision` | 결정할 질문 | 선택지 표 → 연구실 기본 규칙 → 측정 방법 → 관련 페이지 |

front matter: `type`, `audience`, `tags`, `applies_to`(version 범위), `owner`, `last_reviewed`, `sources`, 영어 번역 페이지에만 `source_commit`.

## 4. 작성 기준 요약

전체 표(W1–W18, V1–V11)는 조사 보고서 "작성 기준" 절에 있다. M0에서 `About/작성 기준` 페이지와 Vale 설정으로 만든다.

- 영어 문장 25단어 이하, 한국어 문장 약 60자 이하(경험칙), 문단 5문장 이하.
- 한 문장에 생각 하나. 중요한 것을 먼저 쓴다.
- 능동태. 번역투(-되어지다, "~를 통해", 수행/진행/처리하다)와 메타 담화("앞서 설명했듯이", "간단히")를 쓰지 않는다.
- 같은 개념에 같은 단어. 약어와 전문용어는 처음 나올 때 정의하거나 glossary로 link한다.
- 한국어는 평어체로 쓴다. 영어 번역은 영어 기준(25단어 등)을 따로 검사한다.
- 비유 대신 다섯 기법: 조작적 정의, 관찰 가능한 값(명령과 출력), 대비 표, 실제 숫자로 끝까지 계산한 예, 실제 구성 요소 그림.
- 세대마다 바뀌는 수치는 자릿수와 출처·기준 날짜로 쓴다. 연구실 hardware spec은 쓰지 않는다.
- 그림 규칙: 글만으로 페이지가 성립해야 한다. 그림에는 label을 단다. autoplay와 loop를 쓰지 않는다. clip 하나에 개념 하나. 영상 속 글자는 영어 용어와 identifier만 써서 영상 하나를 두 언어판이 함께 쓴다.
- 한국어 용어: 원어로 쓰고, 처음 나올 때 괄호로 설명을 붙일 수 있다. 음차는 붙이지 않는다. termbase YAML이 금지 음차 목록(커밋, 브랜치, 컨테이너, 레포지토리, 파드 …)을 가지고 Vale가 검사한다.

## 5. 이미지와 출처 정책 요약

1. 공식 페이지로 link하는 것이 기본이다.
2. 그림이 필요하면 사실을 바탕으로 Manim·Mermaid로 다시 그린다. 원본과 다른 layout을 쓰고 "Based on: <URL>"을 단다.
3. CC0, CC BY, MIT, BSD, Apache license 이미지만 복사한다. 그림 아래에 TASL(Title, Author, Source, License) caption을 단다.
4. BY-SA 이미지는 변형한 그 이미지에만 BY-SA를 표시한다.
5. NonCommercial이나 NoDerivatives 조건이 붙은 license와 all-rights-reserved 자료는 복사하지 않는다. NVIDIA 문서, Hugging Face 문서 이미지, Pro Git이 여기에 해당한다.
6. 원문 문장을 옮기지 않고 자기 문장으로 쓴다. 번역도 adaptation이다.
7. 이미지마다 `manifest.yaml` 항목을 두고 CI가 license와 caption을 검사한다.

### 시각화 도구

내용마다 맞는 도구가 다르다. 한 도구로 모두 만들지 않는다.

| 보여줄 내용 | 도구 | 이유 |
|---|---|---|
| 구조와 흐름(실험 실행 경로, 처리 과정, commit DAG, memory 계층) | Manim | 박스와 화살표가 순서대로 나타나고 강조되는 장면을 code로 만든다. conda-forge `manim` 0.22.0으로 Pixi에 고정할 수 있다. |
| 정적인 구조도와 순서도 | Mermaid | 글 안에서 text로 쓰고 diff로 검토한다. render 단계가 없다. |
| 따라 하는 사용법(가짜 terminal, `gsel-compute.yaml` field 설명) | HTML mockup | 명령을 복사할 수 있고, 검색·번역이 되고, text diff로 검토한다. |
| README·발표용 짧은 terminal 녹화 | VHS(`.tape`) | 가짜 CLI가 정제한 고정 출력을 내게 하고 녹화한다. conda-forge `vhs` 0.12.1, `ttyd`, `ffmpeg`. |
| 복사 가능한 terminal 재생 | asciinema | 영상이 아니라 text라 명령을 복사할 수 있다. conda-forge 3.2.1. |
| 사람의 동작(사용자가 workspace를 열고, 실험을 제출하고, 결과를 기다리는 순서) | StykAnimate Python port(만드는 중) | 사람이 무엇을 하는지 보여 준다. Manim scene과 같은 영상 안에 쓸지는 scene 작성자가 정한다. 아래 참고. |
| 쓰지 않는 것 | Motion Canvas, Slidev | Motion Canvas는 npm과 headless browser가 필요해 CI render가 번거롭다. Slidev는 발표용이다. |

StykAnimate Python port(2026-10-29 확인):

- 원본 StykAnimate는 stick figure animation GUI app이다(Electron·WebGPU, JavaScript, GPL-3.0-or-later). Python은 Pivot·Stick Nodes file을 읽는 codec service에만 쓰고, scripting API와 headless render는 없다.
- 계획: engine을 Python으로 porting한 별도 project로 둔다. Manim과 호환되게만 만들고, 둘을 함께 쓸지는 사용자가 정한다.
- handbook에서 쓰려면 port가 다음을 갖춰야 한다.
  - 장면을 Python text source로 쓴다. PR에서 diff로 검토할 수 있다.
  - 화면 없이 명령 하나로 render한다. handbook CI에서 Manim과 같은 방식으로 다시 render한다.
  - conda-forge나 PyPI에서 version을 고정해 설치한다. Pixi environment에 넣는다.
- License:
  - port는 GPL-3.0 저작물의 2차적 저작물이라 GPL-3.0-or-later로 낸다.
  - handbook의 scene source는 MIT로 둔다. MIT는 GPL과 호환되고, handbook repo는 port를 import만 하고 port code를 함께 배포하지 않는다.
  - render한 영상은 program의 출력이라 GPL이 따라오지 않는다. 문서와 같이 CC BY 4.0으로 낸다. 원본 EULA도 export한 animation은 만든 사람 것이라고 한다.
  - community library의 figure·movieclip은 자기 animation 안에서만 쓸 수 있고 file 자체는 재배포할 수 없다. 공개 repo에는 직접 만든 figure만 넣는다.
- 작성 규칙: 인물은 실제 사용자의 동작만 보여 준다. 사물이나 system을 인물로 그리지 않는다(비유 금지).

Manim 사용 규칙:

- `Text`와 `Code`만 쓴다. `MathTex`는 texlive가 필요해 쓰지 않는다.
- `Code`는 Pygments로 문법을 강조하고 줄 단위로 강조할 수 있다. v0.19에서 인자가 바뀌어(`code_string=`) 예전 tutorial의 `code=`, `file_name=`은 동작하지 않는다.
- 영상 속 글자는 영어 용어와 identifier만 쓴다. 그래서 한글 font 없이 영상 하나를 두 언어판이 함께 쓴다. font는 Pixi environment에서 고정한다.
- scene 하나는 30–90초, 개념 하나. 구조가 바뀌면 해당 scene만 다시 render한다.
- scene source 머리에 `# source: <doc> @<commit>`, 끝 화면에 기준 날짜.
- 사용법 mockup에는 쓰지 않는다. terminal과 UI를 직접 그려야 해서 손이 많이 든다.
- 내부 운영 영상은 같은 primitive를 쓰되 운영자용 private repo에서 local render한다. 공개 scene source에 내부 값을 넣지 않는다.

## 6. GitHub 구성

- Project: GSEL Handbook(D6). Fields: `Status`, `Page type`, `Menu`, `Media`(Text / Manim / Mermaid / Mockup), `Language`(en / ko / both), `Track`(Public / Private).
- Labels(handbook): `type: tutorial`, `type: task`, `type: reference`, `type: concept`, `type: symptom`, `type: decision`, `type: infra`, `media: manim`, `media: mockup`, `i18n`, 기존 `question`.
- 주제는 issue label이 아니라 page tag로 관리한다.
- M0, M1은 issue를 하나씩 만든다. M2부터는 milestone마다 tracking issue 하나를 두고 필요할 때 sub-issue로 나눈다.
- 내부 운영 지식과 AI data 정책 issue는 운영자용 private repo에 만든다.

## 7. Milestones와 issues

| # | Milestone | 목표 |
|---|---|---|
| M0 | Foundations | 구조, page template, 두 언어 build, 작성 기준, 이미지 정책 |
| M1 | Media pipeline | Manim·Mermaid·mockup pipeline, pilot 페이지 1개 |
| M2 | Getting started & Compute resources | 첫 경로, 연구실 계산 자원 사용, 관련 증상·결정 페이지 |
| M3 | Concepts: Computer & performance | CPU, memory, GPU, I/O, numeric format |
| M4 | Concepts: OS, network, infrastructure | 외부 문서 확인부터 시작 |
| M5 | Tools | shell, Git/GitHub, Pixi, Hydra, container, editor |
| M6 | Guides: Research practices | 실험 기록, data 관리, debugging, 질문, offboarding |
| M7 | Guides: ML/DL | 결정 페이지로 시작하는 hub |
| M8 | Guides: Geospatial & remote sensing | 기초는 link, 형식·I/O·환경·split은 직접 |
| M9 | AI agents (planned) | 정책 결정 후 착수 |
| — | Maintainer knowledge (private) | 내부 트랙 |

### M0 Foundations

1. **Restructure navigation by reader task** — `type: infra`
   - 3절 메뉴로 재구성. 이동: `onboarding/*` → Getting started, `coder/*` → Compute resources, `reference/glossary.md` → Reference, `reference/system-overview.md` → Compute resources(concept).
   - slug 고정, redirect, lychee 확인.
2. **Page templates and front matter** — `type: infra`
   - 페이지 유형 6개의 template과 front matter. `CONTRIBUTING.md` 갱신.
3. **Writing standard and Vale config (EN/KO)** — `type: infra`
   - W1–W18을 `About/작성 기준`으로. 원본인 한국어는 번역투·메타 담화·음차 regex와 문장 길이 검사. 영어 번역은 Vale Google/Microsoft + readability.
   - 비유 금지와 대체 기법, 평어체 통일.
4. **Termbase and untranslated-term rule** — `type: infra`, `i18n`
   - termbase YAML(`never_translate`, 첫 사용 설명, 금지 음차). Kubernetes ko 관행과 다른 점을 문서에 적는다.
5. **Build the site in English and Korean** — `type: infra`, `i18n`
   - 두 Zensical project(`ko` 원본, `en` 번역), 같은 경로, `extra.alternate` 언어 선택기. D14 URL 배치.
   - 영어 페이지의 `source_commit` 이후 한국어 원본이 바뀌면 CI가 영어 페이지에 banner를 단다. D9 최소 집합 전에는 선택기를 숨긴다.
   - D13: 기존 영어 페이지의 한국어 원본 작성.
   - 확인: 선택기가 같은 페이지로 가는지, 한국어 검색 품질, git 기반 날짜, redirect.
6. **Image and source reuse policy** — `type: infra`
   - 5절 정책, `manifest.yaml`, CI 검사 6개. 문서 license CC BY 4.0(`LICENSE`), 명령·code 예제와 scene·mockup source는 MIT(`LICENSE-CODE`). 어느 부분이 어느 license인지 footer와 `About`에 적는다.
7. **Glossary as tooltips** — `type: reference`
   - `abbr` + snippets 자동 첨부. termbase와 같은 source에서 만든다.
8. **Page tag vocabulary** — `type: infra`
   - 초기 tag: `cpu`, `gpu`, `memory`, `storage`, `network`, `os`, `kubernetes`, `auth`, `shell`, `git`, `github`, `pixi`, `hydra`, `container`, `coder`, `submit`, `debugging`, `data`, `ml`, `geospatial`, `remote-sensing`.
9. **Issue forms for questions and doc requests** — `type: infra`, `question`
   - 질문, 문서 요청, 오류 신고. "같은 질문 두 번 → 문서" 규칙.
10. **Personas and concept map** — `type: infra`
    - D12 persona. concept 페이지 목록과 Manim scene 범위를 정하는 concept map.
11. **Ownership and review cycle** — `type: infra`
    - D10 CODEOWNERS, `last_reviewed` 검사, "Recently updated" 목록.

### M1 Media pipeline

12. **Render Manim scenes in CI** — `type: infra`, `media: manim`
    - Pixi environment로 `manim` 고정(문서 검사 env와 분리). font 고정. LaTeX 미사용.
    - `pages-deploy`에서 render. mp4는 git에 커밋하지 않는다. PR에서는 바뀐 scene만 render해 artifact로 올린다.
13. **Shared visual primitives** — `media: manim`
    - box, arrow, repo, `Pod`, 상태 표시, terminal 창. 영상 속 글자는 영어 용어만.
    - scene 머리에 `# source: <doc> @<commit>`, 끝 화면에 기준 날짜. 내부 정보 없음.
14. **Embed rules for video and diagrams** — `media: manim`
    - label, play·pause, autoplay·loop 금지, poster frame. Mermaid는 caption과 alt text.
    - WCAG 2.2.2, 2.3.1, 2.3.3 원문 확인.
15. **Interactive mockup component** — `media: mockup`
    - 가짜 terminal, `gsel-compute.yaml` editor, 단계 이동, field 설명. 출력은 정제한 고정 text. 아래에 같은 단계를 글로.
16. **Detect mockup drift** — `media: mockup`
    - mockup의 명령과 field가 실제 CLI·schema에 있는지 검사.
    - 열린 문제: schema 원본이 private repo다. private CI에서 검사하거나 공개 schema export가 필요하다.
17. **Pilot: system overview with Manim** — `type: concept`, `media: manim`
    - `system-overview.md` 기반 60초 scene. 두 언어 페이지. pipeline 전체 확인.
18. **Evaluate the StykAnimate Python port for scenes** — `type: infra`, `media: manim`
    - port가 위 세 조건(text source, headless render, version 고정 설치)을 갖춘 뒤 시작한다.
    - Manim scene 하나에 사용자 동작을 넣어 CI render, 두 언어 페이지, license 표시를 확인한다.

### M2 Getting started & Compute resources (tracking issue)

- tutorial: 첫 주 checklist, 첫 workspace, 첫 CPU 실험, 첫 GPU 실험(mockup).
- concept: 연구실 계산 환경 개요, 실험 실행 경로, 실험 처리 과정(검증 → Job → 실행 → log·결과, 실패 분기). Manim.
- reference: `gsel-compute.yaml` field, CLI, 상태 값, Quick reference 한 장.
- task: log·결과 확인, data와 storage 사용 규칙.
- decision: workspace에서 돌릴까 job으로 제출할까, `gpu_memory_gib` 정하기(짧게 실행해 측정한 뒤 여유분), `gpu_count`를 늘릴까, 내 job이 GPU를 쓰는지 확인.
- symptom: `Pending`, `OOMKilled`, `CUDA error: out of memory`, `ImagePullBackOff`, GPU 사용률 0%, workspace가 시작되지 않음. 제목은 실제 출력에서 복사하고 내부 값은 `<placeholder>`.

### M3 Concepts: Computer & performance (tracking issue)

concept 페이지. 각 페이지 끝에 "연구실에서는" section.

| 페이지 | 핵심 | 연결 증상·결정 | Manim 후보 |
|---|---|---|---|
| Latency, bandwidth, throughput | 세 개념 구분, 자릿수 | 모든 "왜 느린가" | 시간 축 확대(ns → ms) |
| Compute-, memory-, overhead-bound | 시간이 어디서 쓰이는가 | 더 큰 GPU가 필요한가, batch를 키울까 | 세 영역 막대 |
| CPU | core, thread, clock, cache, SIMD, Python loop vs NumPy | `cpu` 요청값, 전처리가 느림 | core·thread 배치 |
| Threads, processes, oversubscription | limit보다 많은 thread가 서로 다툰다 | `OMP_NUM_THREADS`, DataLoader worker 수 | core와 thread |
| Memory | hierarchy, page cache, swap, OOM killer | process가 kill됨 | hierarchy |
| GPU | SM, VRAM 용량과 bandwidth, `nvidia-smi` 읽기 | GPU util이 낮음 | 단순 core 병렬 |
| GPU utilization vs saturation | GPU-Util은 kernel이 하나라도 돈 시간 비율이다. SM activity와 다르다 | "100%인데 느리다" | 시간 창과 kernel 막대 |
| GPU 비동기 실행과 sync 지점 | `.item()`, `print`, `.cpu()`가 동기화를 강제한다 | logging으로 느려짐, 시간 측정이 틀림 | CPU queue와 GPU timeline |
| Host ↔ device transfer | PCIe/NVLink, pinned memory, overlap | GPU가 data를 기다림 | 전송 병목 |
| CUDA stack | driver / toolkit / runtime, cuDNN, compute capability, framework version 호환, Pixi `system-requirements` | "no kernel image", version 오류 | 계층 쌓기 |
| GPU memory의 세 숫자 | allocated vs reserved vs `nvidia-smi`, 텐서 밖 memory(CUDA context 등) | `gpu_memory_gib` 정하기, "여유가 있는데 OOM" | 쌓인 막대 |
| VRAM budget | weights, gradients, optimizer state, activations | CUDA OOM | stacked bar 분해 |
| Numeric formats | fp32/tf32/fp16/bf16/int8 범위와 정밀도 | memory·속도·정확도 trade-off | bit field |
| Data 크기 계산 | 행 × 열 × band × byte | RAM·GPU 요청값 | 계산표 |
| Storage & block I/O | 1 pixel을 읽어도 block 전체를 읽는다. local vs network storage, small files | data loading이 느림 | tile grid에서 1 pixel 요청 |
| 압축의 trade-off | CPU decode 비용과 I/O 양 | 공유 storage 용량 | 표 |
| 처리량 측정 | warm-up 뒤 steady state에서 잰다 | 효율 판단, job 길이 추정 | 시간축 그래프 |

CS&E 기초(같은 milestone 후반):

- complexity: 시간·공간 복잡도.
- parallelism & concurrency: multiprocessing, GIL, distributed training 개념.
- numerics: floating point error, reproducibility.
- software engineering: module, test, Ruff, type hint, dependency.
- profiling: 측정 방법.

### M4 Concepts: OS, network, infrastructure (tracking issue)

첫 issue: **Verify upstream docs and public/private boundary.** 보고서의 이 영역 URL은 모두 미검증이다. 각 URL과 license를 확인하고, 페이지마다 공개할 것과 private로 둘 것을 publication policy로 판단한다.

Operating systems:

| 페이지 | 연결 증상·결정 | 공개 | private |
|---|---|---|---|
| Kernel, OS, distribution(Ubuntu LTS) | base image 선택 | 개념, 배포판 이름 | node host OS 세부 |
| Process, signal, exit code | "exit code 137", process kill | 전부 | — |
| Filesystem, 경로, mount, 사라지는 저장 | file이 사라짐, 어디에 저장하나 | 원칙 | 실제 mount 경로 |
| 권한, user·group, UID/GID | `Permission denied`, 공유 directory | 개념, `ls -l` 읽기 | UID/GID 값 |
| 환경 변수, `PATH`, shell 시작 file | `command not found`, 다른 `python`이 실행됨 | 전부 | — |
| apt vs Pixi/conda-forge vs pip | 환경 충돌 | 원칙 | sudo 허용 여부(D11) |
| cgroup과 container resource limit | `nproc`이 limit보다 큼, `OOMKilled` | 개념 | 정확한 limit 값 |
| WSL2 | Windows laptop 사용자의 local 환경 | 전부 | — |
| 문자 encoding, CRLF, 대소문자 | `bad interpreter: ^M`, 한글 file 이름 깨짐 | 전부 | — |
| SSH와 key | SSH key가 동작하지 않음 | 개념, 일반 명령 | host 이름 |

Network와 infrastructure:

| 페이지 | 연결 증상·결정 | 공개 | private |
|---|---|---|---|
| IP, subnet, port, DNS, default gateway | URL이 안 열림 | 개념, 일반 명령 | 실제 대역, hostname |
| "gateway"의 네 뜻 | 용어 혼동 | network default gateway, API gateway, GSEL Compute Gateway, Kubernetes Gateway API의 구분 | Gateway URL, 인증 설정 |
| Intranet, 사설 주소, NAT | 연구실 밖에서 내부 service 접속 불가 | 개념 | 실제 대역, 경계 장비 |
| Network switch, Wi-Fi router | 큰 전송은 유선으로 | 개념, 사용 규칙 | 장비 model, topology |
| NAS와 NFS | small files가 느림, `Permission denied` | 개념, network filesystem 특성, 사용 규칙 | export·mount 경로, 용량, quota |
| VPN | 누가 써야 하는가(D11) | 개념, 역할 | 제품, 구성, 접근 규칙 |
| Cloudflare: domain, DNS, Tunnel, Zero Trust | 브라우저 접속 시 login 화면, 접근 차단 | 개념, sign-in 흐름 | tunnel 이름, Access policy |
| Forward proxy와 egress allowlist | `pixi install`, `git clone` 실패, 허용 요청 절차 | 개념, `HTTPS_PROXY`의 의미, 요청 절차 | allowlist 내용, proxy 주소 |
| SSO, OIDC, LDAP | 로그인 반복, group 권한 반영 | 일반 개념, 사용자 로그인 흐름 | 설정, directory 구조, 비밀번호 절차 |
| Container image, registry, tag vs digest | `ImagePullBackOff` | 개념, 공개 image 이름 | registry credential |
| Kubernetes 기초 | `Pending`, `OOMKilled`, `Evicted` | node, `Pod`, `Job`, request·limit 개념 | namespace, RBAC, node 이름, quota |
| k3s, Helm | — | 이름과 역할 | 구성 |
| GitOps와 Flux | 설정 변경이 바로 반영되지 않는 이유 | reconcile loop 개념 | repo 구조, 배포 절차 |
| Coder | workspace 시작 실패, 재시작 후 file 유지 범위 | 개념, 사용 흐름 | template 내부 |
| GitHub Actions와 runner | CI check가 queued에서 멈춤 | 개념 | runner host |
| Monitoring(Prometheus, Grafana) | 내 job의 GPU 사용률 확인 | 개념, metric 해석 | dashboard URL, alert |
| Cluster vs grid vs cloud | 용어 혼동 | 전부 | — |

### M5 Tools (tracking issue)

- shell & Linux: task 페이지와 Software Carpentry / MIT Missing Semester link.
- Git & GitHub: concept(commit DAG, branch, PR, review, CI check — Manim), task(PR 열기, review 반영, conflict 해결). Pro Git은 NC라 link만.
- Pixi: tutorial(첫 project), task(dependency 추가, task, 다른 사람 repo를 Pixi로 옮기기), reference(요약표), concept(lockfile — Manim, 왜 Pixi인가).
- Hydra: concept(config 합성), task(override).
- container: M4 container·registry 페이지와 합친다. Tools에는 사용 방법만.
- editor: code-server / VS Code.

### M6 Guides: Research practices (tracking issue)

- 실험 기록: commit, config, seed, environment, metric을 실행마다 남긴다.
- data 관리: 원본은 수정하지 않는다, 큰 data의 위치, backup, 공유 storage 규칙.
- 장시간 작업: tmux, checkpoint와 재시작.
- debugging: 오류 문구 읽기, 최소 재현 예제, 확장 전 sanity check.
- 논문 code 재현: 다른 사람 repo를 Pixi 환경으로 옮긴다.
- 결과 정리: figure, table, log.
- 좋은 질문 쓰는 법: 재현 정보를 갖춘 issue(M0-9 form과 연결).
- offboarding: 졸업·이동 시 data와 code 인계.
- 다루지 않는 것 목록과 대신 볼 곳.
- interface가 바뀔 때 transition 페이지를 만드는 규칙.

### M7 Guides: ML/DL (tracking issue)

hub는 결정 페이지("어디서, 몇 개의 GPU로, 얼마의 memory로")로 시작한다.

| 페이지 | 연결 증상·결정 | 깊이 |
|---|---|---|
| 낮은 GPU 사용률 진단 순서 | GPU util이 낮음 | Core |
| DataLoader 조정(`num_workers`, `pin_memory`, `non_blocking`) | data loading이 느림, CPU 요청값 | Core |
| Small files와 shard format | network storage에서 epoch이 느림 | Core |
| Augmentation 위치 | CPU 높고 GPU 낮음 | Short |
| 최대 memory 측정 | `gpu_memory_gib` 측정 단계 | Short |
| CUDA OOM 대응 순서 | CUDA OOM, 더 큰 GPU를 요청할지 | Core |
| Batch size와 learning rate | GPU를 바꾼 뒤 결과가 달라짐 | Core |
| Mixed precision 실무 | fp16에서 NaN | Core |
| Tensor core에 맞는 shape | 특정 크기에서 느려짐 | Short |
| Profiling 도구 선택 | 성능 질문 | Short |
| cuDNN benchmark, `torch.compile` | 첫 step이 느림 | Short |
| 재현성과 seed | 재현 안 됨 | Core |
| Checkpoint와 재개 | `Pod` eviction, 긴 실행 | Core |
| NaN과 학습 불안정 | NaN loss, loss spike | Core |
| 확장 전 sanity check | 버그 있는 실행에 GPU 시간 낭비 | Short |
| Multi-GPU 여부(DDP 먼저) | `gpu_count` 결정 | Short |
| Inference memory | 큰 batch inference의 memory 요청 | Short |
| Parameter·FLOPs 추정 | 제출 전 memory·시간 추정 | Short |

출처가 서로 다른 결론을 내는 곳(gradient accumulation의 속도 이득, byte/param 집계)은 조건을 함께 적는다.

### M8 Guides: Geospatial & remote sensing (tracking issue)

기초(raster vs vector, CRS, 읽기·시각화, crop, zonal statistics)는 Carpentries geospatial-python, AutoGIS, Geocomputation with Python으로 link한다. 직접 쓰는 것은 연구실에서 생기는 실패와 공유 cluster의 결정이다.

| 페이지 | 연결 증상·결정 | 깊이 |
|---|---|---|
| `set_crs` vs `to_crs` | data가 엉뚱한 위치에 찍힘 | Core |
| 축 순서와 폐기된 `+init=` | 점이 뒤집힘 | Core |
| 투영 CRS에서 면적·거리 | 면적·거리 결과가 틀림, 저장 CRS 선택 | Core |
| Datum 변환 grid | 실행마다 결과가 다름, egress가 막힌 job | Short |
| Affine transform | 반 pixel 어긋남 | Short |
| Resampling 방법 | warp 뒤 class 값이 소수가 됨 | Core |
| Block·windowed read, overview | strip TIFF를 tiled로 바꿀지, 미리보기가 느림 | Core |
| COG와 range request | 기본 raster 보관 형식 | Core |
| 압축과 predictor | 공유 storage 용량 | Short |
| GDAL 설정(`GDAL_CACHEMAX`, `GDAL_NUM_THREADS`) | 열기가 느림, `Pod` memory 급증 | Short |
| Zarr chunk, xarray + Dask | chunk 모양 선택, `.values`에서 kernel이 죽음 | Core |
| GeoParquet, FlatGeobuf | 큰 vector·label table 형식 | Short |
| STAC 검색 → data cube | 위성 영상을 재현 가능하게 받기 | Short |
| File format 결정 표 | 어떤 형식으로 저장할까 | Core(decision) |
| Pixi로 GDAL·PROJ 설치, driver plugin | "Driver not found" | Core |
| PROJ data 충돌 | "Internal PROJ Error … SQLite error" | Core(symptom) |
| Band, nodata, dtype과 scale factor | 통계가 망가짐, 변환 후 OOM | Core |
| Processing level(L1/L2/L3) | 어떤 level을 받을지 | Short |
| Band 저장 순서(BSQ/BIL/BIP) | pixel 단위 읽기가 느림 | Short |
| Patch 추출과 sampler | CNN용 tiling, image와 mask의 CRS가 다름 | Core |
| Spatial autocorrelation과 spatial split | train/val/test split 설계 | Core(decision) |
| Band별 정규화 | RGB pretrained weight에 다중 band 입력 | Core |

library version은 Pixi lockfile로 고정하고 페이지에 version을 적는다(TorchGeo sampler 이름이 version마다 다르다).

### M9 AI agents (planned, Backlog)

- 선행: 연구 data, secret, 공유 storage 내용을 외부 service로 보내는 것에 대한 연구실 정책(private repo issue).
- tutorial: workspace에서 Claude Code / Codex 처음 실행, 개인 계정 인증.
- task: code 읽기, refactoring, test 작성, 오류 분석.
- concept: agent가 할 수 있는 것과 사람이 확인해야 하는 것, 결과에 대한 책임.
- 다른 기관의 AI 도구 페이지(CSC, NERSC, FASRC, Kempner)를 참고한다.

### Maintainer knowledge (private)

운영자용 지식과 그 영상은 private repo에서 따로 관리한다. handbook의 공통 visual primitives를 가져다 쓴다.

## 8. 확인할 것

| 항목 | 할 일 |
|---|---|
| M4 영역 upstream URL | 모두 미검증. M4 첫 issue에서 확인 |
| Zensical | 언어 선택기의 같은 페이지 연결, 한국어 검색, git 기반 날짜, redirect를 M0-5에서 시험 |
| Zensical native i18n | 일정 없음. 착수 전 다시 확인 |
| WCAG 2.2.2, 2.3.1, 2.3.3 | M1-14에서 원문 확인 |
| DCGM SM activity 정의 | NVIDIA 문서로 확인. 그림은 다시 그린다 |
| `GDAL_CACHEMAX` 5%의 기준 | host RAM인지 cgroup limit인지 `Pod`에서 확인 |
| NFS small-file 영향 | 연구실 storage에서 측정. 수치는 private, 원칙만 공개 |
| 한국 EPSG code(5186, 5179) | EPSG registry로 확인 |
| CUDA driver·toolkit 호환성 | M3 CUDA stack 페이지 착수 시 조사 |
| 한국어 문장 60자 기준 | 경험칙으로 표시. 국립국어원 자료 확인 |
| mockup drift 검사 schema 출처 | M1-16 |
