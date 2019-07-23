# python day06

### map(), zip(),filter()

- map(function, iterable)
  - iterable의 모든 원소에 function을 적용한 후 결과 반환
  - list, dict, set, str, bytes, tuple, range
- zip(*iterables)
  - 복수 iterable한 것을 모아줌

``` python
# 예시를 봅시다.
girls = ['jane', 'iu', 'mary']
boys = ['justin', 'david', 'kim']

matching = list(zip(girls, boys))
print(matching)
#[('jane', 'justin'), ('iu', 'david'), ('mary', 'kim')]
```

- 둘의 길이가 다르면 
- zip은 반드시 길이가 같을 때 사용해야한다. 가장 짧은 것을 기준으로 구성한다.

```python
a = '1235'
b = '56767'

for digit_a, digit_b in zip(a, b):
    print(digit_a, digit_b)

```

- filter(function, iterable)
  - iterable에서 function의 반환된 결과가 참인 것들만 구성하여 반환

``` python
def even(n):
    return not n%2
result = list(filter(even, numbers))
print(result)
#[2, 4, 6, 8]
```



### OOP(객체지향 프로그래밍)

- oop 객체 지향 프로그래밍: 한 언어에 종속된 것이 아니라 여러 언어에 존재

- 하나의 패러다임임, 여러 개의 독립된 단위

#### 클래스

- 같은 종류의 집단에 속하는 속성(Attribute)와 행위(behavior)를 정의한 것
- 똑같은 무엇인가를 계속해서 만들어 낼 수 있는 설계 도면이며 객체란 클래스로 만든 피조물을 뜻함

``` python
class Cookie:
    pass
```

> 클래스로 만든 객체를 인스턴스이다.

### 인스턴스 
-  인스턴스는 클래스()를 실체화 한 것
-  객체는 자신 고유의 속성이며 클래스에서 정의한 행위를 수행 가능
-  붕어빵 틀은 붕어빵을 만들기 위한 도구! instance: 즉각적으로 생성이된 것
``` python 
인스턴스명 = 클래스()
```
### 속성
- 클래스/인스턴스가 가지고 있는 속성

### 메서드
- 클래스/인스턴스가 할 수 있는 행위


### 클래스 정의하기
- 선언과 동시에 클래스 객체가 생성되며 선언된 공간은 지역 스코프로 사용

### 인스턴스 생성하기
- 인스턴스 객체는 ClassName()을 호출함으로 선언하며 인스턴스 객체와 클래스 객체는 서로 다른 이름 공간을 가지고 있음
- 인스턴스=>클래스=>전역 순으로 탐색

### self: 인스턴스 객체 자기 자신
- javascript의 this 키워드와 동일한 것으로 무조건 메서드에서 self를 첫번째 인자로 설정
- 메서드는 인스턴스 객체가 함수의 첫번째 인자로 전달되도록 되어있음

### 클래스-인스턴스간의 이름 공간
- 클래스를 정의하면 클래스 객체가 생성되며 해당되는 이름 공간이 생성
- 인스턴스를 만들게 되면, 인스턴객체가 생서오디며 해당 이름 공간 생성
- 인스턴스에서 특정한 어트리뷰트에 접근하면 인스턴스=>클래스 순으로 탐색

### 생성자-소멸자
- 생성자는 인스턴스 객체가 생성될 때 호출되는 함수, 소멸자는 객체가 소멸되는 과정에서 호출되는 함수

``` python
class  Person:
    def __init__(self):
        print('생성될 때 자동으로 호출되는 메서드입니다.')
    def __del__(self):
        print('소멸될 때 자동으로 호출되는 메서드입니다.')
```



### 포켓몬 구현
``` python
class Pika: # Pika 클래스 객체 생성
    def __init__(self, name,level): # 생성자 함수로 초기 설정값 부여 이름, 레벨을 따로 선언
        self.name = name
        self.level = level
        self.hp = 20*self.level
        self.exp = 0
       
        print(f"{self.name}야 안녕! 피카피카")
    
    def bark(self): 
        print('pikachu')
    
    def body_attack(self, name): #만약 몸통박치기를 하면 자신의 레벨*5만큼의 위력을 가짐
        if type(name) == Pikachu:
            body = self.level*5
            name.hp = name.hp-body
            if name.hp <= 0: #만약 상대방의 체력이 0이면 경험치를 획득!
                self.exp = name.level*15
                if self.exp <= self.level*100 : #만약 일정 이상의 경험치를 얻으면 레벨 업
                    self.level += 1
                    print(f'{self.name} 레벨 {self.level}!')
                    self.exp =0
                return name.bye(name)
        else:
            print('다시 이름을 쓰세요')
        return f'몸통 박치기로 {body}의 데미지를 주었다!'
    
    def thousand_volt(self, name):  #만약 전기공격을 하면 자신의 레벨*7만큼의 위력을 가짐
        thousand = self.level*7
        name.hp = name.hp-thousand
        if name.hp <= 0: #만약 상대방의 체력이 0이면 경험치를 획득!
            self.exp = name.level*15
            if self.exp <= self.level*100 : #만약 일정 이상의 경험치를 얻으면 레벨 업
                self.level += 1
                print(f'{self.name} 레벨 {self.level}!')
                self.exp = 0
            return name.bye(name)
        return f'십만볼트로 {thousand}의 데미지를 주었다!'
    
    def bye(self, name):
        return f'{self.name}은 쓰러지고 말았다'
```

