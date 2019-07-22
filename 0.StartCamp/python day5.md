# python day5

### List Comprehension(내포)

- list를 만들 수 있는 간단한 방법 
- 세제곱 리스트 만들기

``` python
numbers = range(1, 11)
# 기존의방법
result = []
for i in numbers:
    result.append(pow(i,3))
print(result)

#List Comprehension
cubic_list = [num**3 for num in numbers] #반복문을 활용을 할 수 있음
print(cubic_list)
```

- 짝수 리스트 만들기

``` python
numbers = range(1, 11)
# 기존의방법
result = []
for i in numbers:
    if i%2 ==0:
        result.append(i)
print(result)

# List Comprehension
even_list = [num  for num in numbers if num%2 ==0] 
#조건문을 주어 조건의 참이면 리스트에 담기
print(even_list)
```

- 곱집합

``` python
girls = ['jane', 'iu', 'mary']
boys = ['justin', 'david', 'kim']

# 반복문을 활용하여 만들어주세요.
lists =[]
for i in boys:
    for j in girls:
        pair = (i,j)
        lists.append(pair)
print(lists)

# List comprehension을 활용하여 만들어주세요.
pair = [(x,y) for x in boys
              for y in girls]
#for문을 중첩해서 할 수 있음
print(pair)
```



### 딕셔너리 메소드 활용

#### 추가 및 삭제
- pop(key[, default]) : 
  - key가 딕셔너리에 있으면 제거하고 그 값을 돌려줍니다. 그렇지 않으면 default를 반환
  - default가 없는 상태에서 딕셔너리에 없으면 KeyError가 발생

- .update()
  - 값을 제공하는 key, value로 덮어씀
  - 기존 키가 없으면 아예 추가가 됨
- .get(key[, default])
  - key를 통해 value를 가져옴
  - 절대로 keyerror가 발생하지 않음 default는 기본적으로 None임


###  dictionary comprehension

``` python
# dictionary comprehension
cubic = {i: i**3 for i in range(1,11)}
print(cubic)
#{1: 1, 2: 8, 3: 27, 4: 64, 5: 125, 6: 216, 7: 343, 8: 512, 9: 729, 10: 1000}
```



### 세트 메소드 활용
#### 추가 및 삭제
- add(elem)

	- 출력이 되는 순간 마음대로 나옴
	- 중복이 되지 않음
- .update(*others)
  - 여러 가지의 값 추가
  - iterable한 값을 넣어야함
- .remove(elem)
  - elem을 세트에서 삭제, 없으면 keyerror
- discard(elem)
  - keyerror가 발생하지 않음
- pop()
  - 임의의 원소를 제거 및 반환

### 모듈
- 모듈은 파이썬 정의와 문장들을 담고 있는 파일 
- 모듈을 활용하기 위해서는 반드시 import문을 통해 내장 모듈을 이름 공간에 가져와야함
``` python
# import를 이용하여 fibo.py를 가져옵니다
import fibo
print(dir(fibo)) #fibo를 탐색함
print(fibo.fib(5))
fibo.fib_loop(10)
```
- 함수를 자주 사용할거면, 변수에 할당해서 사용할 수 있음

### 패키지
- 패키지는 점으로 구분된 모듈 이름을 써서 파이썬의 모듈 이름 공간을 구조화하는 방법

#### from 모듈명 impor 어트리뷰트
- 특정한 함수 혹은 어트리뷰트만 활용하고 싶을 때 작성

#### from 모듈명 import *
- 해당하는 모듈 내의 모든 변수, 함수, 클래스를 가져옴

#### from 모듈명 import 어트리뷰트 as
- 자신이 원하는 지정하는 이름을 붙여 가져올 수 있음

### 파이썬 기본 모듈
1)math
함수	비고
math.ceil(x)	소수점 올림
math.floor(x)	소수점 내림
math.trunc(x)	소수점 버림
math.copysign(x, y)	y의 부호를 x에 적용한 값
math.fabs(x)	float 절대값 - 복소수 오류 발생
math.factorial(x)	팩토리얼 계산 값
math.fmod(x, y)	float 나머지 계산
math.fsum(iterable)	float 합
math.modf(x)	소수부 정수부 분리

함수	                비고
math.pow(x,y)	x의 y제곱의 결과
math.sqrt(x)	x의 제곱근의 결과
math.exp(x)	e^x 결과
math.log(x[, base])	밑을 base로 하는 logx (base default 값은 e)

2)datetime
형식 지시자(directive)	의미
%y	연도표기(00~99)
%Y	연도표기(전체)
%b	월 이름(축약)
%B	월 이름(전체)
%m	월 숫자(01~12)
%d	일(01~31)
%H	24시간 기준(00~23)
%I	12시간 기준(01~12)
%M	분(00~59)
%S	초(00~61)
%p	오전/오후
%a	요일(축약)
%A	요일(전체)
%w	요일(숫자 : 일요일(0))
%j	1월 1일부터 누적 날짜

속성/메소드	내용
.year	년
.month	월
.day	일
.hour	시
.minute	분
.second	초
.weekday()	월요일을 0부터 6까지

3)timedelta
- from datetime import timedelta
- 비교 연산이 가능

### 문법 에러
- 가장 많이 만날 수 있는 에러 
	- EOL :다음표 오류
	- EOF:괄호 닫기 오류
- 예외 : 문법이나 표현식이 바르게 되어 있지만 실행시 발생하는 에러
	- zerodivisionerror : 0을 이용해서 나눌 때, 발생되는 에러
	- NameError :정의 되지 않은 변수 사용할 때 발생
	- typeError: 오류가 데이터 유형과 관련된 오류, ex)필수 argument 누락시,  argument가 많을 경우도 있음 
	- valueError : 자료형은 맞는데 값이 틀리면 오류 발생
	- indexError:자료의 범위를 벗어날 때 발생하는 에러
	- keyerror: 컨테이너에 참조가 없을 때 발생하는 에러
	- modukenotfoundError : 잘못된 모듈이 import될 때 에러 발생
	- importError: 이름이 잘못됐거나 모듈이의 경로가 잘못 되었을 때 발생
	- keyboardinterrupt :함수가 실행하고 있는 동안 강제로 종료를 했을 때 발생
	
### 예외 처리
- try, except
  - try구문으로 예외처리를 할 수 있음

    ``` python
    try:	try절 먼저 시행
    	codeblock1
    except 예외: #예외가 중간에 발생하면 남은 부분을 수행하지 않고 except실행
    	codeblock2
    	
    try:
        num = input('숫자를 입력하세요: ')
        print(int(num))
    except ValueError: #valueError가 발생하면 print됨
        print('바보야 숫자를 입력해')
    	
    ```

    

- 복수의 예외 처리 

  - 하나 이상의 예외를 모두 처리

  - 괄호가 잇는 튜플로 여러 개의 예외 지정

    ``` python
    try:
        codeblock1
    except (예외1, 예외2):
        codeblock2
    
    try :
        num = input('100으로 나눌 값을 입력하세요 : ')
        print(100/int(num))
    except (ValueError, ZeroDivisionError): #valueError나 zerodivisionError 발생시 실행됨
        print('바보')
    ```

    

  - 에러는 순차적으로 수행됨 

  - 에러 문구를 함께 넘겨줄 수 있음

  ``` python
  try:
      my_list = []
      print(my_list[100])
  except IndexError as err:
      print(f"{arr}, 오류가 발생")
  ```

- else 

  - 에러가 발생하지 않은 경우 수행되는 문장으 else 사용

  ``` python 
  # else를 사용해봅시다.
  try:
      numbers = [1,2,3]
      number = numbers[2]
  except IndexError:
      print('Error')
  else :
      print(number**2)
  ```

  

- finally 

  - 반드시 수행해야하는 문장 즉, 모든 상황에 실행되어야만 하는 코드

  ``` python
  # finally를 사용해봅시다.
  try:
      fruits = {'apple':'사과','peach':'복숭아'}
      fruits['pineapple']
  except KeyError as err:
      print(f'{err} error')
  finally :
      print('끝')
  ```

  