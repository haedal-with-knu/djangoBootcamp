# 이쁜 게시판 만들기
> 부트스트랩이란 프론트엔트 프레임워크를 활용해 쉽게 웹사이트를 꾸며봅니다

## [부트스트랩](https://getbootstrap.com/)이란?
![bootstrap](img/bootstrap.png)
세계에서 가장 인기 있는 프론트엔드 라이브러리로 자신의 아이디어를 빠르게 구현하는데 도움을 주는 오픈소스 툴킷입니다.

* 모바일, PC, 태블릿 등 다른 크기의 디스플레이에 대응 가능한 반응형 웹
* 미리 만들어진 수많은 컴포넌트
* jQuery를 기반으로 구축된 강력한 플러그인

코드를 만져보며 게시판을 이쁘게 만들어봆니다

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


## `웹서버 실행` 복습  

**프로젝트를 실행할때마다 반복해서 사용하는 명령어입니다**  
파이썬 가상환경 설정 
```console
root@goorm:/workspace/djangoBootcamp/mysite# source myvenv/bin/activate
```
이제 `django` 웹서버를 실행합시다   
구름 IDE를 사용하는 경우  
상단 메뉴바의 `프로젝트 -> 실행 URL과 포트`에서   
80번 포트를 설정 후 접속합니다
```console
(myvenv) root@goorm:/workspace/djangoBootcamp/mysite# python manage.py runserver 0:80 
```

## `Bootstrap` `CDN`
`HTML`에서 `<head>`태그엔 중요한 정보지만   
눈에 보이지 않는 정보들이 포함됩니다.

[`Bootstrap` 홈페이지](https://getbootstrap.com/)에 가면  
`CDN`을 확인 할 수 있습니다  
![img/bootstrapCDN.png](https://github.com/haedal-with-knu/djangoBootcamp/blob/master/img/bootstrapCDN.png)

`Bootstrap` `CDN`을 복사해 `<head>` 태그 안에 아래의 코드를 삽입합니다

아래와 같이 붙이면 됩니다  
`mysite/main/templates/main/index.html`
```html
<html>
    <head>
        <title>Django Tutorial</title>
        <!-- Bootstrap CDN -->
        <!-- Required meta tags -->
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

        <!-- Bootstrap CSS -->
        <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
    </head>
    <body>
        <h1>메인 페이지입니다</h1>
        <!-- 정적 이미지 불러오기 -->
        {% load static %}
        <img src="{% static 'firstImg.png' %}">
    </body>
</html>
```
## [Container](https://getbootstrap.com/docs/4.3/layout/overview/)  
![img/bootstrapContainer.png](https://github.com/haedal-with-knu/djangoBootcamp/blob/master/img/bootstrapContainer.png)

기술의 발달로 PC의 경우는 가로가 넓어지고, 모바일의 경우 세로가 넓어졌습니다.  
웹페이지는 기기들의 다양한 디스플레이에 탄력적으로 대응해야 했습니다.  
[반응형 웹](https://developers.google.com/web/fundamentals/design-and-ux/responsive/?hl=ko)이란 기술로 여러 기기들에 대응하게 됩니다.  
이를 가장 쉽게 이해할 수 있는 개념이 `Container`입니다.  
코드를 입력해보며 손으로 익혀봅니다.

`<body>` 태그 안의 내용을 `<div class=conatiner>`로 감싸봅니다
`mysite/main/templates/main/index.html`
```html
<html>
    <head>
        <title>Django Tutorial</title>
        <!-- Bootstrap CDN -->
        <!-- Required meta tags -->
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

        <!-- Bootstrap CSS -->
        <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
    </head>
    <body>
        <!-- container 사용하기 -->
        <div class="container">
            <h1>메인 페이지입니다</h1>
            <!-- 정적 이미지 불러오기 -->
            {% load static %}
            <!-- 이미지가 디스플레이의 가로보다 긴 경우 max-width 100%로 수정 -->
            <img class ="img-fluid"src="{% static 'firstImg.png' %}">
        </div>
    </body>
</html>
```


### [Grid 시스템(Col, Row)](https://getbootstrap.com/docs/4.3/layout/grid/)
격자(`Grid`) 형식으로 디스플레이를 나누어 콘텐츠들을 배치하는 방식으로  
가로축을 `Col`, 세로축을 `Row`로 나타냅니다

페이스북, 인스타그램에서 많이 본 `Card`형식의 게시글들을 나타내려면  
적당한 크기의 가로로 배치하는 것이 중요합니다.
> 세로로 긴 글은 스크롤을 내리면 되니 문제가 덜 생깁니다

화면의 가로 축을 12칸으로 나누어 기기마다 대응합니다.

디스플레이 마다 대응하기엔 아직 힘드니 PC에서 진행해봅니다.  
`mysite/main/templates/main/index.html`  
`PC 화면`  
![img/col_3_PC.png](img/col_3_PC.png)   
`모바일 화면`  
![img/col_3_sm.png](img/col_3_sm.png)

```html
<html>
    <head>
        <title>Django Tutorial</title>
        <!-- 한국말을 사용하겠다 -->
        <meta charset="utf-8">
        <!-- 화면 너비에 맞게 페이지를 맞추겠다 -->
        <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">
        <!-- Bootstrap CDN -->
        <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
    </head>
    <body>
        <!-- container 사용하기-->
        <div class="container">
            <h1>Grid 공부하기 - Col,Row</h1>
            <!-- Grid 시스템을 사용하겠다 -->
            <div class="row">
                <!-- 3칸짜리 div를 만듭니다. 파란색이고, padding은 3만큼 넣습니다 -->
                <div class="col-sm-3 bg-primary p-3">col-3</div>
                <div class="col-sm-3 bg-primary p-3">col-3</div>
                <div class="col-sm-3 bg-primary p-3">col-3</div>
                <div class="col-sm-3 bg-primary p-3">col-3</div>
                <div class="col-sm-3 bg-primary p-3">col-3</div>
                <div class="col-sm-3 bg-primary p-3">col-3</div>
                <div class="col-sm-3 bg-primary p-3">col-3</div>
            </div>
            
            원래 있던 코드들 ...
            ...
        </div>
    </body>
</html>
```

`col-sm-3`을 `col-3`으로 진행해도 비슷하게 작동합니다.  
`col-sm-3`은 모바일 화면에서 1줄(12칸)을 차지합니다.(540px 미만)  
태블릿, 노트북, 데스크탑에서 3칸으로 적용됩니다(540px 이상)  
`col-3`은 모든 화면에서 3칸으로 적용됩니다.

##### 반응형 웹의 강력함이 느껴지나요?

## [Navbar](https://getbootstrap.com/docs/4.3/components/navbar/)
![img/bootstrapNavbar.png](https://github.com/haedal-with-knu/djangoBootcamp/blob/master/img/bootstrapNavbar.png)  
많은 홈페이지에서 사용하는 상단 메뉴바를 만들어봅니다  
[`Bootstrap` Navbar](https://getbootstrap.com/docs/4.3/components/navbar/)에 들어가 적당한 Navbar을 찾아 코드를 가져와 `<body>`태그 안에 붙입니다.  

저는 아래의 코드를 가져왔습니다.  

`mysite/main/templates/main/index.html` 구조
```html
<html>
    <head>
        <title>Django Tutorial</title>
        !-- Bootstrap CDN -->
        <!-- Required meta tags -->
        <meta ...>

        <!-- Bootstrap CSS -->
        <link ...>
    </head>
    <body>
        <!-- 홈페이지 상단에 nav가 들어갑니다-->
        <nav class="navbar navbar-expand-lg navbar-light bg-light">
            ...
            ... 엄청 길게 들어갑니다
            ... 놀라지 마세요
            ... 원하는대로 수정해봅시다
        </nav>
        <div class="container">
            ...
        </div>
    </body>
</html>
```
수정 후 `mysite/main/templates/main/index.html`  
![img/navbar_index.png](img/navbar_index.png)  
```html
<html>
    <head>
        <title>Django Tutorial</title>
        <!-- Bootstrap CDN -->
        <!-- Required meta tags -->
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

        <!-- Bootstrap CSS -->
        <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
    </head>
    <body>
        <nav class="navbar navbar-expand-lg navbar-light bg-light">
          <a class="navbar-brand" href="#">내 홈페이지</a>
          <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
          </button>

          <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <ul class="navbar-nav mr-auto">
              <li class="nav-item active">
                <a class="nav-link" href="#">메인</a>
              </li>
              <li class="nav-item">
                <a class="nav-link" href="/blog">게시판</a>
              </li>
              <li class="nav-item dropdown">
                <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                  드롭다운
                </a>
                <div class="dropdown-menu" aria-labelledby="navbarDropdown">
                  <a class="dropdown-item" href="#">궁금궁금</a>
                  <div class="dropdown-divider"></div>
                  <a class="dropdown-item" href="#">맘대루 넣읍시다</a>
                </div>
              </li>
              <li class="nav-item">
                <a class="nav-link disabled" href="#" tabindex="-1" aria-disabled="true">뭘 넣을까</a>
              </li>
            </ul>
            <form class="form-inline my-2 my-lg-0">
              <input class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search">
              <button class="btn btn-outline-success my-2 my-sm-0" type="submit">검색하기</button>
            </form>
          </div>
        </nav>
        <!-- container 사용하기 -->
        <div class="container">
            <h1>메인 페이지입니다</h1>
            <!-- 정적 이미지 불러오기 -->
            {% load static %}
            <!-- 이미지가 디스플레이의 가로보다 긴 경우 max-width 100%로 수정 -->
            <img class ="img-fluid"src="{% static 'firstImg.png' %}">
        </div>
    </body>
</html>
```


게시판(`blog.html`)과 세부게시글 페이지(`posting.html`)에도 `CDN`, `navbar`,`container`를 추가합니다  
#### 구조도 
```html
<html>
    <head>
        <title ...>
            <!-- Bootstrap CDN -->
            <!-- Required meta tags -->
            <meta ...>

            <!-- Bootstrap CSS -->
            <link ...>
    </head>
    <body>
        <nav>
            navbar 자리입니다 ...
            ...
        </nav>
        <div class="container">
            원래 body 안의 내용 ...
            ...
        </div>
    </body>
</html>
```
수정 후 `mysite/main/templates/main/blog.html`  
![img/navbar_blog.png](img/navbar_blog.png)
  
```html
<html>
    <head>
        <title>Blog List</title>
        <!-- Bootstrap CDN -->
        <!-- Required meta tags -->
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

        <!-- Bootstrap CSS -->
        <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
    </head>
    <body>
        <nav class="navbar navbar-expand-lg navbar-light bg-light">
          <a class="navbar-brand" href="#">내 홈페이지</a>
          <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
          </button>

          <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <ul class="navbar-nav mr-auto">
              <li class="nav-item active">
                <a class="nav-link" href="#">메인</a>
              </li>
              <li class="nav-item">
                <a class="nav-link" href="/blog">게시판</a>
              </li>
              <li class="nav-item dropdown">
                <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                  드롭다운
                </a>
                <div class="dropdown-menu" aria-labelledby="navbarDropdown">
                  <a class="dropdown-item" href="#">궁금궁금</a>
                  <div class="dropdown-divider"></div>
                  <a class="dropdown-item" href="#">맘대루 넣읍시다</a>
                </div>
              </li>
              <li class="nav-item">
                <a class="nav-link disabled" href="#" tabindex="-1" aria-disabled="true">뭘 넣을까</a>
              </li>
            </ul>
            <form class="form-inline my-2 my-lg-0">
              <input class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search">
              <button class="btn btn-outline-success my-2 my-sm-0" type="submit">검색하기</button>
            </form>
          </div>
        </nav>
        <div class="container">
            <h1>게시판 페이지입니다</h1>
        <!-- 게시판(postlist)의 게시글(list)을 하나씩 보여줍니다 -->
        <!-- {와 %로 이루어진 구문 내부엔 파이썬이 사용됩니다 -->
        <table>
        {% for list in postlist %}
            <!-- 게시글 클릭시 세부페이지로 넘어갑니다-->
            <tr onclick="location.href='https://haedal11233.run.goorm.io/blog/{{ list.pk }}/'">
                <td>{{list.postname}}</td>
                <td>{{list.contents}}</td>
            </tr>
        {% endfor %}
        </table>
        </div>
    </body>
</html>
```

수정 후 `mysite/main/templates/main/posting.html`    
![img/navbar_posting.png](img/navbar_posting.png)  
```html
<html>
    <head>
        <title>Blog List</title>
        <!-- Bootstrap CDN -->
        <!-- Required meta tags -->
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

        <!-- Bootstrap CSS -->
        <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
    </head>
    <body>
        <nav class="navbar navbar-expand-lg navbar-light bg-light">
          <a class="navbar-brand" href="#">내 홈페이지</a>
          <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
          </button>

          <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <ul class="navbar-nav mr-auto">
              <li class="nav-item active">
                <a class="nav-link" href="#">메인</a>
              </li>
              <li class="nav-item">
                <a class="nav-link" href="/blog">게시판</a>
              </li>
              <li class="nav-item dropdown">
                <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                  드롭다운
                </a>
                <div class="dropdown-menu" aria-labelledby="navbarDropdown">
                  <a class="dropdown-item" href="#">궁금궁금</a>
                  <div class="dropdown-divider"></div>
                  <a class="dropdown-item" href="#">맘대루 넣읍시다</a>
                </div>
              </li>
              <li class="nav-item">
                <a class="nav-link disabled" href="#" tabindex="-1" aria-disabled="true">뭘 넣을까</a>
              </li>
            </ul>
            <form class="form-inline my-2 my-lg-0">
              <input class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search">
              <button class="btn btn-outline-success my-2 my-sm-0" type="submit">검색하기</button>
            </form>
          </div>
        </nav>
        <div class="container">
            <h1>게시판 페이지입니다</h1>
        <!-- 게시판(postlist)의 게시글(list)을 하나씩 보여줍니다 -->
        <!-- {와 %로 이루어진 구문 내부엔 파이썬이 사용됩니다 -->
        <table>
        {% for list in postlist %}
            <!-- 게시글 클릭시 세부페이지로 넘어갑니다-->
            <tr onclick="location.href='https://haedal11233.run.goorm.io/blog/{{ list.pk }}/'">
                <td>{{list.postname}}</td>
                <td>{{list.contents}}</td>
            </tr>
        {% endfor %}
        </table>
        </div>
    </body>
</html>
```



## [Card](https://getbootstrap.com/docs/4.3/components/card/)  
![img/bootstrapCard_ex.png](img/bootstrapCard_ex.png)  
휴대폰, '패블릿', 태블릿, 데스크톱, 게임 콘솔, TV, 웨어러블 등 다양한 화면 크기가 존재합니다.  
화면 크기는 항상 변하기 마련이므로, 현재나 미래에 모든 화면 크기에 맞게 사이트를 만드는 것이 중요합니다.  
이에 적응한 대표적인 방식이 `Card`입니다.

`mysite/main/templates/main/index.html`
```html
<html>
    <head>
        <title>Blog List</title>
        <!-- Bootstrap CDN -->
        <!-- Required meta tags -->
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

        <!-- Bootstrap CSS -->
        <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
    </head>
    <body>
        <nav class="navbar navbar-expand-lg navbar-light bg-light">
          <a class="navbar-brand" href="#">내 홈페이지</a>
          <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
          </button>

          <div class="collapse navbar-collapse" id="navbarSupportedContent">
            <ul class="navbar-nav mr-auto">
              <li class="nav-item active">
                <a class="nav-link" href="/">메인</a>
              </li>
              <li class="nav-item">
                <a class="nav-link" href="/blog">게시판</a>
              </li>
              <li class="nav-item dropdown">
                <a class="nav-link dropdown-toggle" href="#" id="navbarDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                  드롭다운
                </a>
                <div class="dropdown-menu" aria-labelledby="navbarDropdown">
                  <a class="dropdown-item" href="#">궁금궁금</a>
                  <div class="dropdown-divider"></div>
                  <a class="dropdown-item" href="#">맘대루 넣읍시다</a>
                </div>
              </li>
              <li class="nav-item">
                <a class="nav-link disabled" href="#" tabindex="-1" aria-disabled="true">뭘 넣을까</a>
              </li>
            </ul>
            <form class="form-inline my-2 my-lg-0">
              <input class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search">
              <button class="btn btn-outline-success my-2 my-sm-0" type="submit">검색하기</button>
            </form>
          </div>
        </nav>
        <div class="container">
            <h1>게시판 페이지입니다</h1>
            <!-- Grid 시스템을 사용하겠다 -->
            <div class="row">
                {% for list in postlist %}
                    <!--태블릿 이상에서 4칸, 모바일에서 1줄(12칸)인 카드-->
                    <div class="col-sm-6">
                        <div class="card" style="width: 18rem;">
                            <!-- 게시글마다 업로드 된 이미지를 보여줍시다 아직은 어렵군요-->
                            {% load static %}
                            <img class ="card-img-top fluid-img"src="{% static 'firstImg.png' %}">
                            <div class="card-body">
                                <h5 class="card-title">{{list.postname}}</h5>
                                <p class="card-text">{{list.contents}}</p>
                                <a href="../blog/{{list.pk}}/" class="btn btn-primary">바로가기</a>
                            </div>
                        </div>
                    </div>
                {% endfor %}
            </div>
        </div>
    </body>
</html>
```

이제 게시물 갯수만큼 카드가 생겼습니다  
확인해봅니다

여러 게시글을 써보고, 화면 크기별로 달라지는 카드를 확인해봅니다  

## 추가 학습
#### [`Theme colors`](https://getbootstrap.com/docs/4.3/getting-started/theming/#theme-colors)  
bootstrap에서 미리 만들어준 palette에서 색을 골라 사용합니다.  
색상을 금방 변경 가능합니다.  
자세한 내용은 문서를 공식문서를 읽어봅니다