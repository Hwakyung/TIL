# Django day1

### Django란?
- Djano란 보안이 우수하고 유지보수가 편리한 웹사이트를 신속하게 개발하는 하도록 도움을 주는 파이썬 웹 프레임워크



- MTV패턴 : MVC 패턴에 대해서 아는가?
  - model : 데이터를 관리
  - template: 사용자가 보는 화면 
  - view: 중간 관리자

- __init__ : 패키지를 인식하게 만듬
- admin : 관리를 해주는 공간
- app: 앱에 대한 설정 공간



```  python
from django.http import HttpResponse


def index(request):
    return HttpResponse("Hello, world. You're at the polls index.")
```

