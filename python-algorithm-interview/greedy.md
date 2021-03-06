# Greedy Algorithm
## 1. 그리디 알고리즘
- 글로벌 최적을 찾기 위해 각 단계에서 로컬 최적의 선택을 하는 휴리스틱 문제 해결 알고리즘
- 탐욕 선택 속성과 최적 부분 구조를 가진 문제들에서 잘 작동함
  - 탐욕 선택 속성 : 앞의 선택이 이후 선택에 영향을 주지 않음
  - 최적 부분 구조 : 문제의 최적 해결 방법이 부분 문제에 대한 최적 해결 방법으로 구성되는 경우
- 반드시 최적 해를 보장하지는 않지만, 합리적인 시간 내에 최적에 가까운 답을 찾아낼 수 있어 유용함
- 예 : 다익스트라, 허프만 코딩, 의사결정 트리 등
## 2. 대표 유형
1. 배낭 문제(짐을 쪼갤 수 없는 경우)
    - 단가가 높은 짐부터 차례대로 채우고 남은 공간은 짐을 쪼개서 담는 방식
2. 동전 바꾸기 문제
    - 큰 단위의 동전을 최대한 활용하는 방식
      - 큰 단위의 동전이 언제나 작은 단위의 동전의 배수이기 때문에, 작은 단위의 동전을 합하여 다른 결과를 도출할 수 없음
      - 그렇지 않은 경우(예를 들어 80원짜리 동전이 있다고 가정)에는 다이나믹 프로그래밍으로 풀어야 함
---------
# Tips
## 1. 힙(Heap)
- 노드들이 *key*(부모노드) &ge; *key*(자식노드)을 만족하는 완전이진트리
- 파이썬은 최소 힙(Min Heap)만 지원함
  - 최소 힙 : 부모 노드의 키 값이 자식 노드의 키 값보다 작거나 같은 완전 이진 트리
  - *key*(부모노드) &le; *key*(자식노드)
- 최대 힙(Max Heap) 형태로 풀이해야 할 경우에는 값을 음수로 변경하여 최소 힙에서 최대 힙처럼 구현하면 됨
## 2. 우선순위 큐(Priority Queue)
- 우선순위를 가진 항목들을 저장하는 큐
- 우선순위 큐는 매번 그때그때의 최소 또는 최댓값을 추출하기 때문에 그리디에 어울리는 대표적인 자료구조임
