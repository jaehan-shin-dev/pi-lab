---
name: workflow-define-goal
description: 목표를 Objective, Requirements, Constraints로 구체화하여 goal.md를 작성한다. Define의 목표 구체화 작업에 사용한다.
---

# Define — Goal 구체화

작업 문서는 현재 작업 폴더 기준 `.goal/<goal>/`에서 관리한다.
`<goal>`은 사용자와 합의한 목표 폴더명을 재사용하고, 대상이 불명확하면 먼저 확인한다.

사용자가 제공한 목표, 현재 상황, 조건을 바탕으로
goal.md를 나열식·계층적으로 작성한다.

- Objective: 궁극적으로 달성하려는 상태
- Requirements: 목표 달성을 위해 만족해야 하는 조건
- Constraints: 목표 달성 과정에서 지켜야 하는 제약

작성 원칙:
- Agent의 임의 해석을 최소화하도록 구체적으로 작성한다.
- 이미 제공된 정보는 활용하고, 부족한 정보만 질문한다.
- 결정이 필요한 항목은 대안과 추천안을 제시하고 확인받는다.
- 독립적인 질문은 Round별로 묶어 Iteration을 최소화한다.

구체적인 해결 방법은 Plan에서 결정한다.
다른 단계는 사용자가 요청할 때만 진행한다.
