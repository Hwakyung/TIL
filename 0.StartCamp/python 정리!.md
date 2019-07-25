#  python 정리!

### python_intro
- 식별자

  - 변수, 함수, 모듈, 클래스 등을 식별하는데 사용되는 이름
  - 일부 예약어는 사용할 수 없음

- 기초 문법

  - 기본적으로 파이썬은 ';' 작성하지 않는다

  - 역슬래시를 사용해서 여러줄 작성 가능

    ``` python
    s = "Hello, "\
        + "my friend. "\
        + "Stay awhile and listen..." 
    print(s) #Hello, my friend. Stay awhile and listen...
    ```

- 수치형

  - init(정수): 10진수가 아닌 8진수: 0o/2진수:0b/16진수:0x로 표현가능
  - math.isclose(a,b): a와 b가 비슷하면 true 아니면 false 반환함 
  - 복소수 : A = 3-4j  a.img(a의 attribute 변수 호출) a.real, a.conjugate()(a의 함수 호출

- container :sequence(ordered) : string(immutable), list(mutable), tuple(immutable),range()(immutable)// unordered: set(mutable),dictionary(mutable)

- mutable 과 immutable

  - mutable 객체 : 객체를 생성한 후, 객체의 값을 수정 가능, 변수는 값이 수정된 같은 객체를 가리키게 됨 ex) list, set, dict
  - immutable 객체: 객체를 생성한 후, 객체의 값을 수정 불가능, 변수는 해당 값을 가진 다른 객체를 가리키게 됨 ex) int, float, complex, bool, string, tuple, frozen, set

- dictionary에서 for 활용하는 4가지 방법

  - dictionary -(key 반복) for key in dict: print(key)
  - key 반복 for key in dict.keys(): print(key)
  - value반복  for value in dict.values(): print(value)
  - key와 value 반복 for key, value in dict.items(): print(key,value)

  

- break 문 
  - 	반복문을 종료하는 표현

- continue 문
  - continue 이후의 코드를 수행하지 않고 다음 요소를 선택해 반복 수행
- else 문
  - else문은 끝까지 반복문 시행한 후 실행