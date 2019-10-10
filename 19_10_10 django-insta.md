## /19_10_10 django-insta

- form.html
  - 사진 파일을 가져오기

``` html
{% extends 'base.html' %}
{% block body %}
<form action="" method="post" enctype="multipart/form-data">
    <!-- 다양한 파일을 저장하기 위해서 enctype을 해줌 -->
    {%csrf_token%}
    <input class="form-control" type="text" name="content">
    <input class="form-control" type="file" name="image" accept="image/*">
    <input class="btn btn-primary" type="submit">
</form>
{% endblock %}
```
- models.py

  - 이미지 썸네일 helper **장고 앱**

  - ProcessedImageField:원본 이미지를 재가공하기 위해서 저장
``` python
from django.db import models
from imagekit.models import ProcessedImageField
from imagekit.processors import ResizeToFill
# Create your models here.
class Feed(models.Model):
    content = models.CharField(max_length=150)
    create_at = models.DateTimeField(auto_now_add =True)
    image = ProcessedImageField(
        processors=[ResizeToFill(300,300)],
        format='JPEG',
        options={'quality':90},
        upload_to='feeds',
    )
```
- feed의 image의 url정보를 가지고 경로를 가져와 화면에 출력하게 함
``` html
{% extends 'base.html'%}
{%block body%}

{% for feed in feeds%}
<div class="card my-2" style="width: 18rem;">
    <img src="{{feed.image.url}}" class="card-img-top" alt="...">
    <div class="card-body">
        <h5 class="card-title">{{feed.content}}</h5>
        <p class="card-text">Some quick example text to build on the card title and make up the bulk of the card's
            content.</p>
        <a href="#" class="btn btn-primary">Go somewhere</a>
    </div>
</div>
{% endfor %}

{%endblock%}
```
-  settings.py
``` python
STATIC_URL = '/static/'
MEDIA_URL= '/media/'
#media 폴더 안에 파일을 저장하게끔 함
MEDIA_ROOT = os.path.join(BASE_DIR,'media')
# 경로를 설정해주는 것 

```