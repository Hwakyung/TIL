# Django day03
- class 선언 후
- 지원하는 모델 필드 타입
  - 주요 Field Types : AutoField, BooleanField, CharField, DateTimeField, FileField, ImageField,TextField
  - 주요 Relation ship Types : ForeignKey, ManyToManyField, OneToOneField

``` python
# Create your models here.
class Question(models.Model):
    title = models.CharField(max_length=50)
    content = models.CharField(max_length=100)
    user = models.CharField(max_length=20)
    created_at = models.DateTimeField(auto_now_add=True)
    #auto now add 자동으로 변수에 저장됨
    
    title = models.CharField(max_length=100) # 길이 제한이 있는 문자열
    content = models.TextField()             # 길이 제한이 없는 문자열
```

#### redirect

```
redirect(to, permanent=False, *args, **kwargs)
```

- `redirect` 는 다음과 같은 파라미터를 가집니다. `to` 에는 어느 URL 로 이동할지를 정하게 됨

- `render` 는 템플릿을 불러오고, `redirect` 는 URL로 이동

``` python 
#html를 필요할 때는 render로 해줌 필요하지 않을 때는 redirect로
    return redirect('/questions/')
```

```python
# 하나의 앱에는 하나의 경로를 분리해서 그룹핑을 해야 함
#마스터 urls에서 하나의 앱에 하나의 경로를 할 수 있게끔 도와줌
urlpatterns = [
    path('admin/', admin.site.urls),
    path('pages/', include('pages.urls')),
    path('utilities/', include('utilities.urls')),
]
```

#### makemigrations

- python manage.py migrations & python manage.py migrate

  - 위 명령을 통해서 앱폴더 아래에 migration 폴더가 생성되고 DB에 테이블을 생성한다.

  - 클래스를 설정할 때 makemigrations를 해야 함 

- migrations
  - 모델 변경내역 히스토리 관리
  - 모델의 변경내역을 DB Schema (데이터베이스 데이터 구조)로 반영시키는 효율적인 방법을 제공

foreign key-외래키

``` html
{%extends 'base.html'%}
{%block body%}
{%for question in questions%}
<h1>{{question.title}}</h1>
<p>{{question.user}}</p>
<p>{{question.content}}</p>
<form action="/questions/{{question.id}}/answers/create/">
  <input type="text" name="content">
  <input type="submit">
</form>
<!--해당 quesetion이 가지고 있는 answer의 set를 다 가지고 오는 명령어 -->
{%for answer in question.answer_set.all%}
<p>{{answer.content}}</p>
{%endfor%}
<hr>
{% endfor %}
{%endblock%}
```

