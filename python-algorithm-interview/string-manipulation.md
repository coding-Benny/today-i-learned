# String manipulation
## 1. 문자열 뒤집기
1. `reverse()`는 리스트에만 제공되는 함수로, 리턴 값 없이 리스트 자신을 뒤집는다.
2.  문자열을 다른 자료형으로 변환하는 과정은 전체적인 연산 속도를 오히려 저하시킬 수 있다.
따라서 `[::-1]`과 같은 **슬라이싱**을 사용하는 것이 지정한 위치의 배열 포인터를 얻어 연결된 객체를 찾아 실제 값을 찾아내어 훨씬 성능을 향상시킬 수 있다.
## 2. 문자열에 ~가 포함되는지 체크
`isalpha()`, `isdigit()`, `isnumeric()`, `isalnum()`과 같은 함수로 문자열에 해당하는 내용이 포함되는지 체크하려면 각각의 문자를 하나하나 체크해야 하지만,
**정규식**을 사용하면 문자열 전체를 한 번에 필터링 할 수 있다.
- `^a-z0-9` : 소문자와 숫자가 아닌 것
> 정규식은 지금 다 공부해서 외워야지..! 보다는 필요할 때마다 쓰면서 익숙해지는 것이 좋다.
## 3. Counter 객체
- 아이템의 개수를 계산해 dictionary로 return
- 키 : 아이템의 값, 값 : 아이템의 개수
- `most_common(int num_to_extract)` : 가장 높은 빈도를 가지는 요소를 `num_to_extract`만큼 추출
## 4. 애너그램 판단하기
- 애너그램 관계인 단어들을 정렬하면 같은 값을 가지게 되므로 정렬한 값을 키로 설정하여 해당하는 단어들을 dictionary에 추가한다.
- `defaultdict()`로 선언하면 항상 디폴트를 생성해 주기 때문에 매번 키 존재 여부를 체크하지 않고 간결하게 구현할 수 있다.
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
## 2. 최적화를 위해 deque 사용 고려하기
- 리스트의 `pop(0)`
  - 첫 번째 원소를 삭제하고 이후 원소들을 빈 칸을 채우기 위해 이동시켜야 하므로 <img src="https://render.githubusercontent.com/render/math?math=O(n)">
  - *n*번 반복하면 <img src="https://render.githubusercontent.com/render/math?math=O(n^2)">
- *deque*의 `popleft()`
  - *deque*은 이중 연결 리스트이므로 <img src="https://render.githubusercontent.com/render/math?math=O(1)">이면 됨
  - *n*번 반복하면 <img src="https://render.githubusercontent.com/render/math?math=O(n)">
- 즉, deque을 사용하면 크게 성능을 향상시킬 수 있다!
## 3. 람다 표현식
- 식별자 없이 실행 가능한 함수
- 별도의 함수 선언 없이 하나의 식으로 함수를 단순하게 표현
- 코드가 길어지고 다른 함수와 섞어서 사용하면 가독성이 떨어지므로 사용에 주의 필요
- `lambda 인자 : 표현식`
- 예 : `(lambda x, y: x + y)(10, 20)` → 30
## 4. List Comprehension
- 간결하고 가독성 높게 표현하는 방법
- `new_list = [expression for_loop_one_or_more conditions]`
```
list_a = [1, 2, 3, 4]
list_b = [2, 3, 4, 5]

common_num = []

for a in list_a:
  for b in list_b:
    if a == b:
      common_num.append(a)
      
print(common_num)  # Output [2, 3, 4]
```
위 코드는 아래와 같이 간결하게 표현할 수 있다.
```
list_a = [1, 2, 3, 4]
list_b = [2, 3, 4, 5]

common_num = [a for a in list_a for b in list_b if a == b]

print(common_num) # Output: [2, 3, 4]
```
## 5. 정렬
- `sorted()` : 숫자와 문자 정렬 가능
  - `key=` 옵션으로 정렬을 위한 키 또는 함수를 지정
  - 다시 문자열로 결합하려면 `join()`
- `sort()` : 리스트 자체를 정렬
  - 제자리 정렬
  - 입력을 출력으로 덮어쓰므로 별도의 추가 공간이 필요하지 않음
  - return 값 없음
### 팀소트(Timsort)
> 퀵 정렬 : 빠르지만 데이터에 따라 편차 큼<br>
병합 정렬 : 일정하게 <img src="https://render.githubusercontent.com/render/math?math=O(nlogn)">정도의 안정적인 성능을 보여 선호
- 파이썬의 정렬 방법이자 현업에서 가장 널리 쓰이는 정렬 알고리즘
- 자바 등의 개발 언어나 안드로이드, 크롬 등의 플랫폼까지 다양하게 영향을 미침
- '실제 데이터는 대부분 이미 정렬되어 있을 것이다'라고 가정하고 설계
  - 이미 정렬되어 있는 경우 비교를 건너뛰므로 성능을 향상시킬 수 있음
- 삽입 정렬과 병합 정렬을 적절히 조합해 사용
## 6. 유니코드와 UTF-8
### ASCII 인코딩 방식
- 초기에 문자를 표현하던 대표적인 방식
- 1바이트에 모든 문자를 표현
  - 이 중 1비트는 체크섬(checksum)
  - 7비트, 즉 128 글자로 문자를 표현
- 한글이나 한자 같은 문자(2바이트)는 정상적으로 표현하기 어려움
### 유니코드
- ASCII 인코딩 방식의 문제를 해결하기 위해 등장
- 2~4바이트의 공간에 여유있게 문자를 할당
  - 1바이트로 표현이 가능한 영문자도 2바이트 이상의 공간을 사용함에 따라 **메모리 낭비**가 심함
### UTF-8
- 유니코드의 문제를 해결하여 효율적으로 인코딩하는 **가변 길이 문자 인코딩** 방식
- 시작 비트를 보고 문자의 전체 바이트를 결정 가능<br>
  ![What is UTF8? - Quora](https://qph.fs.quoracdn.net/main-qimg-205fc8ec38b29683dd8632a1a66cfa88)
- 유니코드 값에 따라 가변적으로 바이트를 결정하여 불필요한 공간 낭비 절약
### 파이썬의 인코딩 방식
- python3부터 유니코드로 모든 문자열을 표현하지만 내부적으로 UTF-8 인코딩을 사용하지 않음
- 파이썬은 원하는 문자에 인덱스로 접근하는 다양한 방식을 제공하는데, 문자열을 UTF-8로 인코딩해둔다면 각 문자마다 바이트 길이가 달라져 전체 문자열을 스캔하지 않으면 원하는 인덱스를 통해 개별 문자에 빠르게 접근하기 어렵기 때문
- 고정 길이 인코딩 방식이 필요해 문자열 단위로 다른 고정 길이 인코딩 방식을 적용함으로써 문제를 해결
-----------------------
## 참고 용어
### 1. 팰린드롬(Palindrome)
- 앞뒤가 똑같은 단어나 문장
- 뒤집어도 같은 말이 되는 단어 또는 문장
- 예 : 기러기, 토마토, 이효리(?)
### 2. 애너그램(Anagram)
- 문자를 재배열하여 다른 뜻을 가진 단어로 바꾸는 것
- 예 : 내 힘들다 → 다들 힘내, stressed → dessert
