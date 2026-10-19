---
name: workflow-plan-eval
description: process.md에서 점검이 필요한 작업을 골라 과정의 평가 기준, 방법, 시점을 process-eval.md에 정의한다. Plan의 과정 평가 설계에 사용한다.
---

# Plan — Process Evaluation

작업 문서는 현재 작업 폴더 기준 `.goal/<goal>/`에서 관리한다.
`<goal>`은 사용자와 합의한 목표 폴더명을 재사용하고, 대상이 불명확하면 먼저 확인한다.

process.md를 기반으로 평가가 필요한 작업을 식별하고,
process-eval.md를 작성한다.

각 항목에 대해 대응하는 작업과 다음 내용을 명시한다.

- Criteria: 실행 과정에서 만족해야 할 조건
- Method: 평가 방법과 점검 시점

각 항목에 평가가 필요한 이유를 설명하고,
결정이 필요한 사항은 사용자 확인을 통해 확정한다.
process.md가 없거나 필요한 내용이 부족하면 사용자에게 확인한다.

과정 점검은 Execute에서, 목표 달성 여부의 최종 평가는 Verify에서 진행한다.
다른 단계는 사용자가 요청할 때만 진행한다.
