# python day3

### 기본값
- 함수가 호출될 때, 인자를 지정하지 않아도 기본 값 설정 가능하다.
- default는 non default 뒤쪽으로 설정해주는 것이 논리 구조상 알맞다.



### 키워드 인자

- 키워드 인자를 활용한 뒤에 위치 인자를 활용할 수는 없다.
- 키워드 인자는 직접적으로 변수의 이름으로 특정 인자를 전달할 수 있다.



### 가변 인자 리스트

- 정해지지 않은 임의의 숫자의 인자를 받기 위해서는 가변인자를 활용

- tuple 형태로 처리 되며, ''*"로 표현됨

  ``` pyth
  def func(*args)
  ```
> print('안녕','안녕하세요','반갑습니다',sep='!') 에서 sep은 구분을 위한 문장



### 정의되지 않은 키워드인자들 처리하기

- 정의되지 않은 인자들은 dict형태로 처리되며, **로 표현하기
- 내부적으로 어떤 데이터가 들어가도 dict형태로 전환되어 반환된다.



### dictionary를 인자로 넘기기
-**dict를 통해 함수에 인자를 넘길 수 있다.
``` python 
def user(username, password, password_con):
    if password == password_con :
        print(f"{username}님 가입되었습니다.")
    else :
        print("비밀번호가 일치하지 않습니다.")

my_account = {
    'username': '홍길동',
    'password': '1q2w3e4r',
    'password_confirmation': '1q2w3e4r'
}

user(**my_account)
```

### 이름공간 및 스코프
- 변수에서 값을 찾을 때 아래와 같은 순서대로 이름을 찾아나갑니다.

1) Local scope: 정의된 함수
2) Enclosed scope: 상위 함수
3) Global scope: 함수 밖의 변수 혹은 import된 모듈
4) Built-in scope: 파이썬안에 내장되어 있는 함수 또는 속성

``` python 
g_num = 3 # 굳이 전역에 있는 변수를 바꾸고 싶다면, 아래와 같이 선언할 수 있습니다.
def g_func():
    global g_num 
    g_num = 5
    print(g_num)
g_func()
print(g_num)
```

- built-in scope :파이썬이 실행된 이후부터 끝까지
- global scope :모듈이 호출된 시점 이후 혹은 이름 선언된 이후부터 끝까지
- Local/Enclosed scope : 함수가 실행된 시점 이후부터 리턴할때 까지