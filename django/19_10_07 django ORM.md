### 19_10_07 django ORM

- $ pip install django-extensions
  - settings에 django_extensions 추가

- $ python manage.py shell_plus 실행

#### 게시물 불러오기
```python
Question.objects.get(id=1)
#있는 데이터만 찾아옴 -> 없을 시, 에러

In [5]: Question.objects.get(id=1)
Out[5]: <Question: Question object (1)>

In [6]: question = Question.objects.get(id=1)
```

#### 댓글 생성

``` python
In [6]: question = Question.objects.get(id=1)
    
In [8]: answer = Answer() #인스턴스 생성
In [14]: answer.content = 'This is comment' #content안에 정보 입력

In [16]: answer.content
Out[16]: 'This is comment'

In [17]: answer.question = question #question의 id값 연결
    
In [18]: answer.question
Out[18]: <Question: Question object (1)>

In [19]: answer
Out[19]: <Answer: Answer object (None)>

In [20]: answer.save()

In [25]: Answer.objects.create(content='두번째 댓글',question = question)
Out[25]: <Answer: Answer object (2)>
```

#### 댓글정보

pk :고유값

``` python
In [32]: answer.question_id #answer가 가지고 있는 아이디 값
Out[32]: 1
    
In [34]: answer.question.id #question이 가지고 있는 아이디 값
Out[34]: 1
```

#### 1:N

- Question(1)=>Answer(N) : `answer_set`

  ``` python
  In [43]: question.answer_set.all()
  Out[43]: <QuerySet [<Answer: Answer object (1)>, <Answer: Answer object (2)>]>
  ```

  - `question.answer`로는 가져올 수 없음.
  - 항상 복수가 전제이기 때문에  QuerySet으로 출력됨
  - answer값이 없을 수 있기 때문에 하위에 저장만 하면 됨

- Answer(N)=>Question(1)  :`question`

  ``` python
  In [42]: answer.question
  Out[42]: <Question: Question object (1)>
  ```

  - 하위의 것은 상위의 정보가 항상 필요로 함

``` python
In [40]: question.answer_set
Out[40]: <django.db.models.fields.related_descriptors.create_reverse_many_to_one_manager.<locals>.RelatedManager at 0x212eba2dac8>
  
#Answer.objects 를 호출한 것과 같음
```

