# python day02

### 조건문
- if문은 조건식과 함께 사용
- 들여쓰기를 항상 주의해야 한다.
- elif은 2개 이상의 조건문을 활용할 때 사용된다.
``` python
if 조건식 :
	수행할 문장1 #조건식이 참이면 문장1 출력 들여쓰기 주의!!
elif 조건식 : #아니면 다음 조건 판단
	수행할 문장2
else :
	수행할 문장3
```

####  조건 표현식
```python
  true_value if <조건식> else false_value
```

- 삼항 연산자와 동일
``` python 
num = 2
value = '홀수입니다.' if num%2 else "짝수입니다." 
print(value)
```



### 반복문



#### while문

- 조건식이 참이면 반복한다. <종료조건을 반드시 설정해줘야 무한루프에 빠지지 않는다!>

``` python 
while True :
    수행할 조건
```



#### for문

- 정해진 범위 내에서 순차적으로 코드를 실행

``` python 
  for i in sequence :
      수행할 문장
```
-for문은 조건문과 함께 활용할 수 있다.

``` python
#1부터 30까지 숫자 중 홀수만 리스트에 담는 코드
lists= []
for i in range(1,31) :
    if i%2 == 1:
        lists.append(i)
print(lists)
```

- index와 함께 `for`문 활용
- `enumerate()`를 활용하면, 추가적인 변수를 활용할 수 있음
  
  - enumerate()은 파이썬 내장함수며 열거 객체를 돌려준다.
  - enumerate(sequence, start) 구성이며 start를 통해 인덱스 시작값을 조절할 수 있다.
- dictionary 반복문

  - key 또는  value를 이용하여 반복문을 사용할 수 잇음

```python 
  dictionary에서 for 활용하는 4가지 방법
  # 0. dictionary (key 반복)
  for key in dict:
      print(key)
  
  # 1. key 반복
  for key in dict.keys():
      print(key)
  
  # 2. value 반복    
  for val in dict.values():
      print(val)
  
  # 3. key와 value 반복
  for key, val in dict.items():
      print(key, val)
```

  

### break, continue, else

### break
 - 반복문을 종료하는 표현



### continue
- continte 이후의 코드를 수행하지 않고 다음 요소로 진행



### else 
- else문은 끝까지 반복문을 시행한 이후에 실행

### 함수

- 재사용, 효율적인 목표와 더불어 코드를 깔끔하게 만들기 위해서 사용한다.

-  함수 선언  def로 시작하여 : 로 끝나며 매개변수로 넘겨줄 수 있으며 동작후 return으로 값을 반환한다.
- dir(__builtins__)으로 내장함수 목록을 볼 수 있다.

``` python
height = 30
width = 20
# 아래에 코드를 작성하세요.
def square(h, w):
    x = h*2 + w*2
    y = h*w
    return f'직사각형 둘레: {x}, 면적: {y}입니다.'
square(30, 20)
```

- 함수의 return 
  - 어떤 종류의 객체여도 상관없으며 오직 한개의 객체만 반환된다.

- 함수의 기본값 :
  - 함수가 호출될 때, 인자를 지정하지 않아도 기본 값을 설정 가능하다.