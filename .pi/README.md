# 이 프로젝트의 subagent 예제

설치된 `@earendil-works/pi-coding-agent` 1.3.0의 `examples/extensions/subagent`를 이 프로젝트에 복사했습니다. 전역 `~/.pi/agent` 설정은 변경하지 않았습니다.

## 구성

```text
.pi/
├── extensions/subagent/
│   ├── index.ts                 # subagent 도구와 실행·화면 표시
│   └── agents.ts                # 역할 설정 탐색
├── agents/
│   ├── scout.md                 # 코드 조사
│   ├── planner.md               # 계획 작성
│   ├── reviewer.md              # 코드 리뷰
│   └── worker.md                # 구현·실행
└── prompts/
    ├── scout-and-plan.md        # scout → planner
    ├── implement.md             # scout → planner → worker
    └── implement-and-review.md  # worker → reviewer → worker
```

## 시작

이 프로젝트 루트에서 pi를 실행하고, 프로젝트 리소스 신뢰 여부를 묻는 경우 내용을 확인한 뒤 승인합니다.

```bash
cd /Users/sinjaehan/DEV/pi-lab
pi
```

이미 실행 중이라면 `/trust`에서 이 프로젝트의 신뢰 여부를 설정한 뒤 `/reload`로 리소스를 다시 불러오세요. 저장된 신뢰 결정은 이후 이 폴더에서 시작하는 pi 프로세스에도 적용됩니다.

일회성으로 이 프로젝트의 리소스를 승인해 시작하려면:

```bash
pi --approve
```

`--approve`는 해당 프로세스에만 적용됩니다. 자식 pi에도 프로젝트 extension·프롬프트 등의 로드를 유지하려면 저장된 프로젝트 신뢰 결정이 필요합니다. 전역 신뢰 설정은 이 설치 과정에서 변경하지 않았습니다.

## 첫 요청

pi 입력창에 다음처럼 요청하세요.

```text
subagent 도구로 planner를 한 번 호출해줘.
현재 폴더의 AGENTS.md를 읽고 작업 절차와 주의점을 요약해줘.
파일은 수정하지 마.
```

실제 `subagent` 도구 호출이 나타나는지 확인하세요. `Ctrl+O`로 결과를 펼치고, 기본 작업 중단 키인 `Esc`로 중단을 요청할 수 있습니다.

## 워크플로 단축 입력

```text
/scout-and-plan 현재 subagent 구현의 구조를 조사하고 개선 계획을 작성해줘
```

- `/scout-and-plan <작업>`: 조사와 계획만 수행합니다.
- `/implement <작업>`: 조사 → 계획 → 실제 구현까지 연결합니다.
- `/implement-and-review <작업>`: 구현 → 리뷰 → 후속 수정을 연결합니다.

`/implement`는 계획 뒤에 사용자 승인을 반드시 기다리지 않습니다. 파일 변경 전 계획을 확인하려면 `/scout-and-plan`으로 나누어 진행하세요.

## 원본과 달라진 두 가지

1. **기본 agentScope를 `project`로 변경했습니다.** 이 프로젝트의 `.pi/agents` 역할을 별도 인자 없이 찾습니다. `user` 또는 `both`를 명시하는 기능은 그대로입니다.
2. **네 역할의 model 지정을 제거했습니다.** 부모의 현재 모델과 thinking level을 상속합니다. 특정 모델을 쓰고 싶다면 해당 역할의 frontmatter에 `model:`을 다시 지정하세요.

그 외 단일·병렬·체인 실행, 역할별 도구, 진행 상황 표시, 오류 처리는 동봉 예제를 유지했습니다. 역할 파일은 매 호출마다 다시 탐색하며, extension·프롬프트를 바꾸면 `/reload`하세요.

## 주의

- 자식은 새 프로세스와 새 대화로 실행하지만 파일과 사용자 권한은 공유할 수 있습니다. 중단해도 파일 변경은 자동 복구되지 않습니다.
- 재위임 금지나 깊이 제한을 추가하지 않았습니다. 자식에서도 extension과 subagent 도구가 로드·활성화되면 재위임이 가능하며, 기본 worker는 별도 도구 목록을 지정하지 않습니다.
- 병렬 호출당 최대 8개 작업, 내부 동시 실행 최대 4개 제한은 전체 자손 수 제한이 아닙니다.
- 모델·인증은 기존 pi 설정을 사용합니다. API 키나 별도 의존성 설정을 이 프로젝트에 추가하지 않았습니다.

## 원본 위치

```text
/opt/homebrew/lib/node_modules/@earendil-works/pi-coding-agent/examples/extensions/subagent/
```

루트의 `pi-subagent-guide.html`은 원본 예제를 설명하는 가이드입니다. 그 문서의 사용자 공통 설치 경로·기본 user 범위 대신, 이 설치에서는 프로젝트 경로·기본 project 범위를 사용합니다.
