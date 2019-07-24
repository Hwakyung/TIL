# python day07

### OOP 파트 2

- 클래스 변수 
  - 클래스의 속성으로 클래스 선언 블록 최상단에 위치 

``` python
class TestClass:
    class_varibale= '클래스변수'
  
TestClass.class_variable #'클래스 변수'
TestClass.class_variable = 'class variable'
```

> 인스턴스=>클래스=>전역 순서로 네임스페이스를 탐색하기 때문에, 접근하게 됨

- 인스턴스 변수
  - 인스턴스의 속성으로 메서드 정의에서 self.instance_variable로 접근 및 할당
  - 인스턴스가 생성된 후 instance.instance_variable로 접근/할당

``` python
class TestClass:
    def __init__(self, arg1, arg2):
        self.instance_var1 = arg1
        self.instance_var2 = arg2
        
    def status(self):
        return self.instance_var1, self.instance_var2
tc = TestClass(1,2)
tc.instance_var1 #1
tc.instance_var2 #2
tc.status#(1,2)
```

- 예시!

```python
# 확인해 봅시다.
class SamSung:
    money = 4000 #클래스 변수
    def __init__(self, location, major): #인스턴스 변수
        self.location = location
        self.major = major
    
    def status(self):
        return self.location, self.major
    
SamSung.money = 4500
SamSung.money #4500  
samsungman1 = SamSung('광주', '경영')
samsungman1.location #광주
```

- 인스턴스 메서드
  - 인스턴스가 사용할 메서드로 클래스로 생성한 인스턴스의 멤버함수를 동작한다고 할 수 있음
  - 첫 번재 인자로 self를 받도록 정의 
- 클래스 메서드
  - 클래스가 사용할 메서드로 정의 위에 @classmethod를 사용하며 첫 번재 인자로 cls를 받도록 정의

``` python
class MyClass:
      @classmethod
      def class_method_name(cls, arg1, arg2, ...):
```

- 스태틱 메서드
  -  클래스가 사용할 메서드로 정의 위에 @staticmethod를 사용하며 인자 정의가 자유로움

``` python
class MyClass:
    @staticmethod
      def static_method_name(arg1, arg2, ...):
          ...
```

```python
class MyClass:
    def instance_method(self):
        return self
    
    @classmethod
    def class_method(cls):
        return cls
    #CLS 알아서 넣어주는 것
    @staticmethod
    def static_method(arg):
        return arg

mc = MyClass()

# 인스턴스 입장에서 확인해 봅시다.
mc.instance_method()
mc.instance_method() == mc
print(mc.class_method()) # <class '__main__.MyClass'>
mc.class_method() == MyClass
print(mc.static_method(123)) # 123

인스턴스는 3가지 메서드 모두 접근할 수 있지만 클래스메서드와 스태틱메서드는 호출하지 말아야함
인스턴스가 할 행동은 인스턴스 메서드로 한정!
```



### 연산자 오버라이딩

- 파이썬에 기본적으로 정의된 연산자를 직접적으로 정의하고 활용


``` python
# 사람과 사람을 같은지 비교하면, 이는 나이가 같은지 비교한 결과를 반환하도록 만들어봅시다.
class Person:
    population = 0
    
    def __init__(self, name,age):
        self.name = name
        self.age = age
        Person.population += 1
    
    def __gt__(self, other):
        if self.age > other.age :
            return True
        else :
            return False
        
p1 = Person('노인', 100)
p2 = Person('아기', 5)
p1 < p2 #False
```



### 상속 

-  클래스에서 가장 큰 특징은 상속으로 부모 클래스의 모든 속성이 자식 클래스에게 상속됨으로 코드의 재사용성이 높아짐!
- 상속은 공통된 속성이나 메소드를 부모 클래스에 정의하고 이를 상속 받아 다양한 형태의 인스턴스를 만들 수 있음.

``` python
# 인사만 할 수 있는 간단한 사람 클래스를 만들어봅시다.
class Person:
    population = 0
    def __init__(self, name='사람'):
        self.name = name 
        Person.population += 1
        
    def greeting(self):
        print(f"안녕하세요 {self.name}입니다.")
        
p1 = Person('chang')
p1.greeting() #안녕하세요 chang입니다.

# 사람 클래스를 상속받아 학생 클래스를 만들어봅시다.
class Student(Person):
    def __init__(self, studnet_id, name= '사람'):
        self.student_id = studnet_id
        self.name = name

# 학생을 만들어봅시다.
s = Student(123456, '김싸피') #안녕하세요 김싸피입니다.

# 진짜 상속관계인지 확인해봅시다.
issubclass(Student, Person) #True
```



### super()

- 자식 클래스에 메서드를 추가 구현 가능
- 부모 클래스의 내용을 사용하고자 할 때, super()를 사용 가능

``` python
# 이를 수정해봅시다.
class Person:
    
    brain = True
    
    def __init__(self, name, age, number, email):
        self.name = name
        self.age = age
        self.number = number
        self.email = email 
        
    def greeting(self):
        print(f'안녕, {self.name}')
        
    def walk(self):
        print('뚜벅뚜벅')
class Student(Person):
    def __init__(self,name, age, number, email, student_id):
        super().__init__(name, age, number, email) 
        self.student_id = student_id
        
p1 = Person('홍길동', 200, '0101231234', 'hong@gildong')
s1 = Student('학생', 20, '12312312', 'student@naver.com', '190000')

p1.greeting() #안녕, 홍길동
s1.greeting() #안녕, 학생
```

- 메서드의 오버라이딩

``` python
# 군인은 다른 인사를 합니다.
class Soldier(Person):
    #super를 통해서 기존의 ㅈ
    def __init__(self,name, age, number, email, army_id):
        super().__init__(name, age, number, email)
        self.army_id = army_id
    def sir(self):
        print(f'충성! 이병 {self.name}')
    def walk(self):
        print('성큼성큼')
        
s1 = Soldier('굳건이',20, 123123,'email@email.com',123456)
s1.greeting() # 안녕, 굳건이
s1.sir()#충성! 이병 굳건이
s1.walk()#성큼성큼
s1.brain # True
```

- 상속관계에서이 이름공간
  - 기존에 인스턴스 ->클래스순으로 이름 공간을 탐색해나가는 과정에서 상속관계는 instance -> class->global 로 확장해감
  - 인스턴스->자식 클래스->부모 클래스->전역

- 다중 상속
  - 두 개 이상의 클래스를 상속받는 경우, 다중상속이 됨.