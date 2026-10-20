---
name: workflow-plan-process
description: goal.md와 goal-eval.md를 바탕으로 전략, 작업 분해, 역할을 process.md에 설계한다. Plan의 실행 과정 설계에 사용한다.
---

# Plan — Process 설계

작업 문서는 현재 작업 폴더 기준 `.goal/<goal>/`에서 관리한다.
`<goal>`은 사용자와 합의한 목표 폴더명을 재사용하고, 대상이 불명확하면 먼저 확인한다.

goal.md와 goal-eval.md를 기반으로
process.md를 작성한다.

- Strategy: 목표 달성을 위한 접근 방식
- Decomposition: 실행 가능한 작업과 의존관계
- Responsibility: AI / User / Collaborative 역할 구분

가장 단순한 AI 전략(Interaction → Task → Agent)부터 검토한다.
복잡한 문제는 실행 가능한 작업 단위로 나누어 진행할 수 있도록 설계한다.

설계 결정은 `workflow-grill` 스킬을 로드해 Round로 묻고, Round마다 process.md를 갱신한다.
설계 중 드러난 목표 수준의 결정은 사용자와 확인해 goal.md에 반영한다.
입력 문서가 없거나 필요한 내용이 부족하면 사용자에게 확인한다.

여기서는 실행 과정을 설계하며, 실제 작업은 Execute에서 수행한다.
다른 단계는 사용자가 요청할 때만 진행한다.
