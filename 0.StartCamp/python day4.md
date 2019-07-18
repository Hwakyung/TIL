# python day4

function을 만드는 경우 local scope 

built in scope global scope local scope 캡슐화를 할 것임

객체를 만드는 경우는 안에 있는 객체를 보존하기 위해서임

### 재귀함수

-재귀 함수는 함수 내부에서 자기 자신을 호출하는 함수를 뜻한다.

``` python
def factorial(n):
    if n <=1 :
        return n
    else :
        return factorial(n-1) *n
```

- 재귀함수를 작성시에는 반드시, `base case`가 존재 하여야 한다.
  - 분할해서 나가다가 특정 숫자를 return을 하는 등의 base case가 필요 (명시적으로 반복)
- `base case`는 점점 범위가 줄어들어 반복되지 않는 최종적으로 도달하는 곳이다.

``` python
def fib(n):
    if n <= 1:
        return 1
    else :
        return fib(n-1) +fib(n-2)
```

```python
RecursionError: maximum recursion depth exceeded #재귀적으로 코드를 짤 때는 1000번 넘으면 안됨
```

- 재귀보다 for문이 빠르지만 알고리즘 자체가 재귀적인 표현이 자연스러운 경우와 재귀 호출로 변수 사용을 줄일 수 있다.

### 문자열 메소드 
- 변형
	1).capitalize() : 앞글자를 대문자로 만듬
	2).title() : 어포스트로피나 공백 이후 대문자 변환
	3).upper() : 모두 대문자 반환
	4)lower) :모두 소문자
	5)swapcase():대 <->소문자로 변경하여 변환
	6)join(iterable): 문자열을 합침
	7)replace(old,new,count) :바꿀 대상 글자를 새로운 글자로
	8)strip() : 공백 제거 lstrip()왼쪽 공백 제거 rstrip()오른쪽 공백 제거



- 탐색 및 검증
   1)find(x):x의 첫번째 위치 반환 없으면, -1
	2)index(x):x의 첫번째 위치 반환 없으면 오류 발생(value error)
	
	3)split(): 문자열을 특정한 단위로 나누어 리스트로 반환

> dir('number')이나 dir('string')을 통해서 다양한 메소드를 확인할 수 있음



- 값 추가 및 삭제

  1)append(x):리스트에 값을 추가

  2)extend(iterable) :리스트의 값을 붙일 수 있음 *여러 값을 추가 할 수 있다!

  3)remove(X) :리스트에서 값이 x을 삭제

  4)insert(i,x):정해진 위치 i에 값을 추가

  5)pop(i): 정해진 위치 i에 있는 값을 삭제하고 항목 반환


- 탐색 및 정렬

  1)count(x):원하는 값의 갯수를 확인 가능 
  
  2)sort():정렬 원본list를 변형시키고 None을 리턴
  
  3)reverse():반대로 뒤집어줌
  
  
  
- 복사

  ``` python
  # 리스트 복사를 해봅시다.
  original_list = [1, 2, 3]
  copy_list = original_list
  print(original_list) #[1,2,3]
  print(copy_list)#[1,2,3]
  
  # b의 값을 바꾸고 a를 출력해봅시다.
  copy_list[0] =123
  print(original_list)#[123,2,3]
  print(copy_list)#[123,2,3]
  
  # id 값을 확안해봅시다.
  print(id(original_list)) #2067325443208
  print(id(copy_list)) #2067325443208
  
  ```

  

  - 딕셔너리와 리스트는 같은 아이디 즉 주소 값을 바라 보고 있음

    ``` python
    # 리스트를 복사해봅시다.
    a = [1,2,3]
    b= a[:]#수정하더라도 원본 데이터는 그대로 있음
    b[0]= 123
    print(a)
    
    # 2차원 배열을 복사해봅시다.
    a=[1,2,[9,10]]
    b = list(a)
    b[2][0] = 9999 #  앞의 list만 복사가 되버림 얕은 복사가 되버림
    print(a)
    
    # 깊은 복사를 사용해봅시다.
    import copy
    a = [1,2,[9,10]]
    b = copy.deepcopy(a)#a전체를 복사
    b[2][0] = 9999
    print(a) #원본 데이터는 그대로 유지됨
    ```

    

copy(): 리스트 복사 가능

clear() :리스트의 모든 항목 삭제
