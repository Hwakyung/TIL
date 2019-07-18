# python Day1

 ### 파이썬



1.매우 쉽다

2.강력하다

	- pip install 등 여러가지 패키지들을 설치되어있는 곳
	- tensorflow 등으로 유명해짐
3.빠르다(효율적임)
4.텍스트 에디터나 터미널등을 이용해서 사용할 수 있음.
5.idle :파이참 통합개발환경 
6.jupyter 셀 단위로 실행가능
7.서버를 띄우는 것과 똑같음 
8.어떤 코드를 먼저 실행하냐에 따라 실행이 됨



### 주석

- 주석이란?
- 

``` if 4 in [1,2,3,4]: print('4가 있다!')

​``` python
def mysum():
    """
    이것은 덧셈 함수 입니다!
    이 줄은 실행 안됨
    다만 docstring인 이유는 있습니다.
    """
    print("더했당!")
```
### 변수 및 자료형
- 변수는 =을 통해 할당

#### 수치형(numbers)
1.int(정수) :모든 정수는 `int`로 표현
2.오버플로우 : 표현할 수 있는 수의 범위를 넘어가는 연산을 하게 되면, 기대햇던 값이 출력되지 않는 현상, 즉 메모리가 차고 넘쳐 흐르는 현상
3.float : 실수는 float로 표현
4.bool : 파이썬에는 `True`와 `False`로 이뤄진 `bool` 타입이 있다. (T,F만 대문자!!)
비교/논리 연산을 수행 등에서 활용
5.None : 파이썬에서는 값이 없음을 표현하기 위해 None타입이 존재

#### 문자형
- 이스케이프 문자열
예약문자  내용(의미)
	\n	      	줄바꿈
	\t		  탭
	\r		 캐리지리턴
	\0 		널(Null)
	\\		\
	'	단일인용부호(')
	"	이중인용부호(")
- String interpolation
1) %-formatting

2) str.format()

3) f-strings : 파이썬 3.6 버전 이후에 지원 되는 사항입니다.

### 연산자
- 산술 연산자 : +,-,%,/

- 비교 연산자 : 

| 연산자 |   내용 |
| -----: | -----: |
|  a > b |   초과 |
|  a < b |   미만 |
| a >= b |   이상 |
| a <= b |   이하 |
| a == b |   같음 |
| a != b | 같지않 |



- 논리 연산자 :

| 연산자 |   내용 |
| -----: | -----: |
|  a > b |   초과 |
|  a < b |   미만 |
| a >= b |   이상 |
| a <= b |   이하 |
| a == b |   같음 |
| a != b | 같지않 |

- 복합 연산자 :

- |  연산자 |       내용 |
  | ------: | ---------: |
  |  a += b |  a = a + b |
  |  a -= b |  a = a - b |
  |  a *= b |  a = a * b |
  |  a /= b |  a = a / b |
  | a //= b | a = a // b |
  |  a %= b |  a = a % b |
  | a **= b | a = a ** b |

### 기초 형변환(Type conversion, Typecasting)

- 파이썬에서 데이터타입은 서로 변환할 수 있다.

1)명시적 형변환

2)암시적 형변환

### 시퀀스(sequence) 자료형

`시퀀스`는 데이터의 순서대로 나열된 형식을 나타낸다.
파이썬에서 기본적인 시퀀스 타입은 다음과 같다.

1. 리스트(list)
2. 튜플(tuple)
3. 레인지(range)
4. 문자열(string)
5. 바이너리(binary) : 따로 다루지는 않습니다.