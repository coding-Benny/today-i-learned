# String manipulation
## 1. 문자열 뒤집기
1. `reverse()`는 리스트에만 제공되는 함수로, 리턴 값 없이 리스트 자신을 뒤집는다.
2.  문자열을 다른 자료형으로 변환하는 과정은 전체적인 연산 속도를 오히려 저하시킬 수 있다.
따라서 `[::-1]`과 같은 **슬라이싱**을 사용하는 것이 지정한 위치의 배열 포인터를 얻어 연결된 객체를 찾아 실제 값을 찾아내어 훨씬 성능을 향상시킬 수 있다.
-------------------------------
# Tips
## 1. 리스트 복사
`=`로 리스트를 복사하려고 하면 두 변수가 같은 객체(리스트)를 참조하게 된다. 이에 따라 어떤 하나의 리스트를 수정하면 함께 수정된다.
만약 원본 리스트는 남겨두고 새로운 리스트를 수정하고 싶다면, `copy()`를 사용해 복사한 후 수정하면 된다.
> 복사를 위해 [:]를 사용하는 것이 문자열이나 리스트를 복사하는 가장 파이썬다운 방식이라고 한다..!
  ```
  # =로 복사하는 경우
  old_list = [1, 2, 3]
  new_list = old_list

  # add an element to list
  new_list.append('a')

  print('New List:', new_list)  # New List: [1, 2, 3, 'a']
  print('Old List:', old_list)  # Old List: [1, 2, 3, 'a']


  # copy()를 사용하여 해결!
  old_list = [1, 2, 3]
  new_list = old_list.copy()  # 또는 new_list = old_list[:]

  new_list.append('a')

  print('New List:', new_list)  # New List: [1, 2, 3, 'a']
  print('Old List:', old_list)  # Old List: [1, 2, 3]
  ```
## 2. 문자열에 ~가 포함되는지 체크
`isalpha()`, `isdigit()`, `isnumeric()`, `isalnum()`과 같은 함수로 문자열에 해당하는 내용이 포함되는지 체크하려면 각각의 문자를 하나하나 체크해야 하지만,
**정규식**을 사용하면 문자열 전체를 한 번에 필터링 할 수 있다.
- `^a-z0-9` : 소문자와 숫자가 아닌 것
> 정규식은 지금 다 공부해서 외워야지..! 보다는 필요할 때마다 쓰면서 익숙해지는 것이 좋다.
## 3. 최적화를 위해 deque 사용 고려하기
*n*번 반복할 때<br>
- 리스트의 `pop()` : <img src="https://render.githubusercontent.com/render/math?math=O(n^2)">
- deque의 `popleft()` : <img src="https://render.githubusercontent.com/render/math?math=O(n)">
으로 deque을 사용하면 크게 성능을 향상시킬 수 있다!
