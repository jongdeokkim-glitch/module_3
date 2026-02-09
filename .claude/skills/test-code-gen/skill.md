---
name: test-code-gen
description: 작성된 커널 코드에 대해 단위 테스트를 수행하는 테스트 코드 생성
---

# test-code-gen skill 사용법

## 테스트 코드에 포함할 내용
 - step 1. 인터럽트 구간에서 사용하면 안되는 함수가 사용되었는지 확인
 - step 2. 단일 코어, 다중 코어 각각에 맞는 함수가 사용되었는지 확인
 - step 3. 마지막 else가 없는 경우 오류가 발생하는지 확인
 - step 4. namespace 구분이 정확히 되었는지 확인
 - step 5. 입력값 및 출력값 정합성 검증
 