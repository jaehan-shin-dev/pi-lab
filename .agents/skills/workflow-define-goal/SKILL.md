---
name: workflow-define-goal
description: workflow-grill로 사용자를 인터뷰해 목표를 Objective, Requirements, Constraints로 구체화하고 goal.md를 작성한다. Define의 목표 구체화 작업에 사용한다.
---

# Define — Goal 구체화

작업 문서는 현재 작업 폴더 기준 `.goal/<goal>/`에서 관리한다.
`<goal>`은 사용자와 합의한 목표 폴더명을 재사용하고, 대상이 불명확하면 먼저 확인한다.

`workflow-grill` 스킬을 로드해, 사용자가 제공한 목표·현재 상황·조건에서 출발해 인터뷰하고,
결과를 goal.md에 나열식·계층적으로 기록한다.

- Objective: 궁극적으로 달성하려는 상태
- Requirements: 목표 달성을 위해 만족해야 하는 조건
- Constraints: 목표 달성 과정에서 지켜야 하는 제약

tree는 목표 수준에 머문다. Objective / Requirements / Constraints의 미결정이 질문 대상이다.
Round마다 goal.md를 갱신하고, 합의·미결정·가정을 구분해 적는다.

구체적인 해결 방법은 Plan에서 결정한다.
다른 단계는 사용자가 요청할 때만 진행한다.
