# 이미지 업로드
> 만들자 영차영차

# [기본적인 게시판 만들기](https://github.com/haedal-with-knu/djangoBootcamp/blob/master/dashboard.md) 코드 가져오기

`기본적인 게시판 만들기` 강의에서 만든 코드를 정리해두었습니다  
가져옵니다  
```console
root@goorm:/workspace/djangoBootcamp# git clone https://github.com/kei01138/bootCamp_Week3
```

`bootCamp_Week3` 폴더 내부의 `mysite` 폴더를 `bootCamp_Week3`,`manage.py`와 같은 위치에 있도록 밖으로 꺼냅시다  
`변경 후`
```
.
|-- bootcamp_Week3
    |-- ...
|-- mysite
|-- manage.py
|-- README.md
```
마우스로 왼쪽의 폴더 트리에서 꺼내도 되고,  
리눅스 커맨드를 이용해 꺼내도 됩니다  
```console
root@goorm:/workspace/djangoBootcamp# mv bootCamp_Week3/mysite/ /workspace/djangoBootcamp/mysite
```


## `가상환경` 실행  

이제 익숙하게 실행하죠?  
`mysite`폴더 들어가서  
```console
root@goorm:/workspace/djangoBootcamp# cd mysite
```
가상환경 실행  
```console
root@goorm:/workspace/djangoBootcamp/mysite# source myvenv/bin/activate
```

## 이미지 업로드
사진이 들어갈 부분을 추가합니다  
게시글 모델에 사진이 들어갈 변수를 정하고,  
기존의 게시글엔 사진값에 `NULL`값을 넣습니다.  

`mainphoto = models.ImageField(blank=True, null=True)`  
파이썬 코드로 어렵지 않죠?

##### `mysite/main/models.py`
```python
from django.db import models

class Post(models.Model):
    postname = models.CharField(max_length=50)
    # 게시글 Post에 이미지 추가
    mainphoto = models.ImageField(blank=True, null=True)
    contents = models.TextField()
    
    # postname이 Post object 대신 나오기
    def __str__(self):
        return self.postname
```

모델을 수정한 후 사진을 처리할 수 있는 라이브러리를 설치해야 합니다.  
`Pillow`를 사용하며 아래와 같이 설치할 수 있습니다.  

```console
(myvenv) root@goorm:/workspace/django/mysite# pip3 install pillow==2.9.0
```
```console
(myvenv) root@goorm:/workspace/django/mysite# python3 manage.py makemigrations
```
```console
(myvenv) root@goorm:/workspace/django/mysite# python3 manage.py migrate
```
```console
(myvenv) root@goorm:/workspace/django/mysite# python3 manage.py runserver 0:80
```
![pillow_install](img/pip3Pillow.png)  
![img_migration](img/makemigration_migrate.png)  

`pillow` 라이브러리 설치 완료

##### change post
![change_post_with_img](https://github.com/kei01138/djangoProject/raw/master/img/change_post_with_img.png)
##### add post
![add_post_with_img](https://github.com/kei01138/djangoProject/raw/master/img/add_post_with_img.png)

#### 사진이 저장될 공간 설정
##### `mysite/tutorialdjango/settings.py`
`setting.py`파일 제일 아래에 추가합니다
```python
MEDIA_ROOT = os.path.join(BASE_DIR, 'media')
MEDIA_URL = '/media/'
```

파일이 저장되는 공간을 추가했지만 아직 `django`가 파일 경로를 찾지 못합니다  
이를 확인해봅니다

게시글 세부페이지에서 확인합니다  
![img_url](https://github.com/kei01138/djangoProject/raw/master/img/img_url.png)   

이렇게 에러가 납니다  
![img_url_error](https://github.com/kei01138/djangoProject/raw/master/img/img_url_error.png)  

이미지의 경로를 설정해 가져옵시다

##### `mysite/tutorialdjango/urls.py`

```python
from django.contrib import admin
from django.urls import path
# index는 대문, blog는 게시판
from main.views import index, blog, posting

# 이미지를 업로드하자
from django.conf.urls.static import static
from django.conf import settings

urlpatterns = [
    path('admin/', admin.site.urls),
    # 웹사이트의 첫화면은 index 페이지이다 + URL이름은 index이다
    path('', index, name='index'),
    # URL:80/blog에 접속하면 blog 페이지 + URL이름은 blog이다
    path('blog/', blog, name='blog'),
    # URL:80/blog/숫자로 접속하면 게시글-세부페이지(posting)
    path('blog/<int:pk>/', posting, name='posting'),
]

# 이미지 URL 설정
urlpatterns += static(settings.MEDIA_URL, document_root=settings.MEDIA_ROOT)
```

이제 업로드한 사진이 뜹니다  
![img_url_ex](https://github.com/kei01138/djangoProject/raw/master/img/img_url_ex.png)

##### `mysite/main/templates/main/postdetails.html`
게시글마다 이미지를 보여줍니다
```html
<html>
    <head>
        <title>Posting!</title>
    </head>
    <body>
        <h1>게시글 개별 페이지입니다</h1>
        <p>{{post.postname}}</p>
        <p>{{post.contents}}</p>
        <!-- 이미지 보여주기 -->
        {% if post.mainphoto %}
            <img src = "{{ post.mainphoto.url }}" alt="" height="600">
            <br>
        {% endif %}
        <a href="https://자기URL넣자/blog/">blog</a>
    </body>
</html>
```
이미지가 뜬 걸 확인합니다  
![postdetails_with_img](https://github.com/kei01138/djangoProject/raw/master/img/postdetails_with_img.png)   

고생 많으셨습니다

