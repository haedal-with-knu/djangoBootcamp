# 프론트엔드 입문

나도 이쁘게 웹페이지 만들고 싶다!  
하지만 공대생인 저에겐 힘든 여정이였습니다.

오픈소스를 설명할때 비유한 벽돌집 기억나시나요?  
벽돌부터 굽기엔 너무나 먼 여정이였습니다.  

트위터에서 만든 프론트엔드 라이브러리 [부트스트랩](https://getbootstrap.com/)을 사용해  
트위터를 닮은 웹페이지를 만들어봅니다

![img/bootstrap.png](img/bootstrap.png)


[HTMl에 대해 궁금하다면?](https://developer.mozilla.org/ko/docs/Learn/HTML/Introduction_to_HTML/Getting_started)  
위 문서를 읽으시면 `HTML`의 구조에 대해 이해되실 겁니다.  
파고들면 엄청난 양의 정보를 맛보실테니 필요한 것만 찾고 넘어가시면 됩니다.  
1. HTML의 전체적인 구조롤 이루는 `<html>`,`<head>`,`<body>` 태그 등
2. 내가 원하는 영역을 나누는 `<div>`,`<nav>`,`<section>` 태그 등
3. 글을 쓸 `<h1>`,`<p>` 태그 등  

이것 말고도 수많은 태그들이 있지만  
다 알고 프로그래밍하긴 불가능합니다.  
필요할 때마다 찾아 씁시다.

지난 [2A. 첫 페이지 만들기](https://github.com/haedal-with-knu/djangoBootcamp/blob/master/firstPage.md)에서 만든 페이지는 이쁘다기엔 부족합니다
`mysite/main/templates/main/index.html`
```html
<html>
<head>
    <title>Django Tutorial</title>
</head>
<body>
    <h1>메인 페이지입니다</h1>
    <!-- 정적 이미지 불러오기 -->
    {% load static %}
    <img src="{% static 'haedal_logo.png' %}">
</body>
</html>
```

## 이쁘게 꾸며봅니다
트위터의 벽돌(`Bootstrap`)을 사용하기 위해 처음엔 `CDN`으로 시작합니다.  
`CDN`은 세계 여러 곳에 코드를 저장해둔 서버 정도로 생각합니다.  

#### `Bootstrap` `CDN`
`HTML`에서 `<head>`태그엔 중요한 정보지만   
눈에 보이지 않는 정보들이 포함됩니다.

[`Bootstrap` 홈페이지](https://getbootstrap.com/)에 가면  
`CDN`을 확인 할 수 있습니다  
![img/bootstrapCDN.png](img/bootstrapCDN.png)

`Bootstrap` `CDN`을 복사해 `<head>` 태그 안에 아래의 코드를 삽입합니다

아래와 같이 붙이면 됩니다  
`mysite/main/templates/main/index.html`
```html
<html>
    <head>
        <title>Django Tutorial</title>
        <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">
    </head>
    <body>
    ...
    </body>
</html>
```

### [`Bootstrap` Navbar](https://getbootstrap.com/docs/4.3/components/navbar/)
많은 홈페이지에서 사용하는 상단 메뉴바를 만들어봅니다  
[`Bootstrap` Navbar](https://getbootstrap.com/docs/4.3/components/navbar/)에 들어가 적당한 Navbar을 찾아 코드를 가져와 `<body>`태그 안에 붙입니다.  

저는 아래의 코드를 가져왔습니다.  
![img/bootstrapNavbar.png](img/bootstrapNavbar.png)

`mysite/main/templates/main/index.html`
```html
<html>
    <head>
        <title>Django Tutorial</title>
        <link ...>
    </head>
    <body>
        <!-- 홈페이지 상단에 nav가 들어갑니다-->
        <nav class="navbar navbar-expand-lg navbar-light bg-light">
            ...
            ... 엄청 길게 들어갑니다
            ... 놀라지 마세요
        </nav>
        <h1>메인 페이지입니다</h1>
        <!-- 정적 이미지 불러오기 -->
        {% load static %}
        <img src="{% static 'haedal_logo.png' %}">
    </body>
</html>
```






