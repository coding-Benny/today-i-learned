# Binary Search
## 개념
- 정렬된 배열에서 값을 찾아내는 알고리즘
- 값을 찾아내는 시간 복잡도가 ![My Formula](https://latex.codecogs.com/gif.latex?O%28logn%29)
- 예: 7번 이내로 관객이 선택한 숫자를 찾아내는 카드 마술
  - 중간 값을 기준으로 크고 작은지를 판별해 값을 찾아나감

## 1. 이진 검색
<ol>
  <li>재귀 풀이</li>
  <ul>
    <li>파이썬에는 재귀 호출에 대한 호출 횟수 제한(default는 1000)이 있음</li>
    <li>원한다면 제한 횟수를 늘일 수 있지만, 일반적으로 코딩 테스트 플랫폼에서는 변경을 허용하지 않으므로, 가급적 1000번 이내에 풀이가 가능하도록 구현해야 함</li>
      <ul>
        <li><del>최근 HackerRank에서 진행한 코테에서 값을 변경하여 Test case 하나 더 통과시키긴 했지만,, 의도에 맞지 않은 풀이였다.</del></li>
      </ul>
  </ul>
  <li>반복 풀이</li>
  <ul>
    <li>대부분의 재귀 풀이는 반복 풀이로 변경할 수 있음</li>
    <li>좀 더 직관적이라 이해하기 쉬움</li>
  </ul>
  <li>이진 검색 모듈</li>
  <ul>
    <li><code>bisect</code> 모듈을 제공하여 파이썬다운 방식으로 간단하게 풀이 가능</li>
  </ul>
  <li>index 풀이</li>
  <ul>
    <li><code>index()</code> 메소드를 활용해서 존재하지 않는 값이면 <code>ValueError</code> 발생</li>
    <li>이진 검색을 요구하는데 이렇게 풀이해서는 경우에 따라 페널티를 받을 수 있음</li>
  </ul>
</ol>
  
#### 이진 검색 vs. `index()`
- `index()`는 앞에서부터 차례대로 찾아 최악의 경우 ![My Formula](https://latex.codecogs.com/gif.latex?O%28n%29)으로, 뒤에 위치한 값일수록 점점 속도가 느려짐
- 이진 검색은 ![My Formula](https://latex.codecogs.com/gif.latex?O%28logn%29)으로, 항상 일정한 속도를 보임
- 따라서 배열의 크기가 크고, 찾아야 하는 값이 항상 앞에만 있는 것이 아니라면 `bisect`를 적극 활용하자!
