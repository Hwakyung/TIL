# Django day03
- post와 get방식의 차이 
  - post : 포스트의 정보를 처리해주는 것으로 데이터의 변화
  - get : 있는 데이터를 가져오는 것으로 기존의 정보를 주는 것 

- CSRF :사이트 간 요청 위조(또는 크로스 사이트 요청 위조, 영어: Cross-site request forgery, CSRF, XSRF)는 웹사이트 취약점 공격의 하나로, 사용자가 자신의 의지와는 무관하게 공격자가 의도한 행위(수정, 삭제, 등록 등)를 특정 웹사이트에 요청하게 하는 공격

``` html
{% extends 'base.html'%} {% block body %}
<h1>post-ping!</h1>
<form action="/post-pong/" method="POST">
  {% csrf_token %} 
  <input type="text" name="username" />
  <input type="password" name="password" />
  <input type="submit" value="login" />
</form>
{% endblock %}
```

- static 파일

``` html
{% extends 'base.html'%} {% load static %} {% block body %}
<link rel="stylesheet" href="{% static 'css/style.css'%}" />
<h1>파이리</h1>
<img src="{% static 'image/test.jpg' %}" alt="" />
{% endblock %}

<!--정적 파일들을 프로덕션 환경에서 쉽게 제공 할 수있는 단일 위치로 수집-->
```

``` python
# 하나의 앱에는 하나의 경로를 분리해서 그룹핑을 해야 함
#마스터 urls에서 하나의 앱에 하나의 경로를 할 수 있게끔 도와줌
urlpatterns = [
    path('admin/', admin.site.urls),
    path('pages/', include('pages.urls')),
    path('utilities/', include('utilities.urls')),
]
```

#### 장고 모델
- 뷰(view) 함수에서 데이터베이스에 어떤 작업을 요청할 때는 SQL 구문이 필요하다.

- 데이터들의 집합이 데이터베이스

- ORM 파이썬을 중간에 번역을 해줘서 SQL문으로 바꿔줌

​	CRUD 

### Django 설치 순서
	1. 폴더 생성 : mkdir 폴더이름
	2. 폴더로 이동 : cd 폴더 이름
	3. 가상환경생성 : python -m venv venv
	4. 가상환경 활성화 : source venv/Scripts/activate
	5. pip로 django설치 : pip install django
	6. 프로젝트 만들기 : django-admin startproject 프로젝트 이름
	7. 개발 서버 확인 : python manage.py runserver
	8. 앱 생성하기 : django-admin startapp 앱이름

클래스를 설정할 때 makemigrations를 해야 함

CharField의 특징