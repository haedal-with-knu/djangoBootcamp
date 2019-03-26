# Instagram PC버전 만들어보자
> html, css를 이용하여 만들어봅니다.

## 1. Header를 만들어보자
> Header에는 로고와 검색창 그리고 nav가 들어갑니다.


우선 `index.html`파일을 하나 만들어봅시다.
```html
<!DOCTYPE html>
<html>
<head>
    <title>instagram</title>
</head>
<body>
    <header>
        <div class="logo">
            
        </div>
        <div class="search">
           
        </div>
        <nav>
            
        </nav>
    </header>
</body>
</html>
```
`<header>`에 2개의 `div`와 `nav`를 만들어줍니다.<br>
첫 번째 `div`에 `class="logo"`
두 번째 `div`에 `class="search"`라고 이름을 지어줍니다.

```html
<div class="logo">
    <img src="images/instagrams.png" alt="" class="instagram_logo">
</div>
```
`img`를 넣어주고 `class="instagram_logo"`라는 이름을 붙여줍니다. <br>
나중에 이 `class`이름을 통해 크기를 조정할 수 있어요.

```html
<div class="search">
    <input type="text" value="검색">
</div>
```
`input`을 통해 사용자의 입력을 받을 수 있도록 합니다.


```html
<nav>
    <ul>
        <li><img src="images/compass.svg" alt="" class="logo_img"></li>
        <li><img src="images/heart.svg" alt="" class="logo_img"></li>
        <li><img src="images/profile.svg" alt="" class="logo_img"></li>
    </ul>
</nav>
```
`ul`과 `li`를 통해 nav를 만듭니다. <br>
인스타를 보면 이미지로 되어있죠? 우리도 이미지를 넣어보도록 하겠습니다.<br>
그리고 크기를 조절하기 위해 `class="logo_img"`라는 이름을 미리 붙여줍니다.<br>


`html`로 밑그림을 다 그렸으니 이제 색칠을 해봐야겠죠?<br>
`css`작업을 해보도록 합시다.<br>

### 1-2. Header CSS 작업하기

`style.css`파일을 만들어 줍니다.
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <title>instagram</title>
    <link rel="stylesheet" href="./style.css">
</head>
</html>
```
`html`파일의 `head`부분에 `<link rel="stylesheet" href="./style.css">`로 파일을 불러옵니다.<br><br>

`style.css`파일에서
```css
body{
    margin:0;
    padding:0;
    background-color: #fafafa;
}
header{
    height: 80px;
    display: flex;
    justify-content: space-evenly;
    align-items: center;
    border-bottom: 1px solid #DBDBDB;
    background-color: #ffffff;
}
.instagram_logo{
    width: 165px;
}
.search input{
    width: 200px;
    padding: 5px;
    border:1px solid #DBDBDB;
    border-radius: 5px;
    background-color:#fafafa;
    text-align: center;
    color: #999999;
}
.logo_img{
    width: 25px;
    padding: 10px;
    padding-right: 0;
}
ul{
    display: flex;
    list-style: none;
}
li{
    margin-right: 25px;
}
```
`header`에 `display:flex;`를 적용시켜 준 후, `justify-content`와 `align-items`를 통해 가로 세로 정렬을 해줍니다.<br>
그리고 아까 지정해놓은 `class`를 통해 각 이미지의 크기 및 여백을 지정해 줍니다.

![./img/Header.PNG](./img/Header.PNG)

이러게 나오면 header는 완성!!!



## 2. content 만들어보기 
> `display:flex`를 이용하자

```html
<body>
    <header>
    ...
    </header>
    <div class="con_wrap">
        <div class="conA">
            ...
            ...instagram의 contents 내용이 들어갑니다.
        </div>
        <div class="conB">
           ...
           ...profile, story, 추천 친구 목록이 들어갈거에요.
        </div>
    </div>
</body>
```
내용이 들어갈 `div` 2개를 만들어 준 후,
`div class="con_wrap"`으로 감싸줍니다.

### 2-1. con_wrap CSS 작업하기

```css
.con_wrap{
    display: flex;
    justify-content: center;
    align-items: flex-start;
    margin-top: 50px;
    padding: 0 290px;
}
.conA{
    flex: 2;
    margin: 10px 0;
}
.conB{
    flex: 1;
}
```
`div class="con_wrap"`에 `display:flex;`를 적용하여 내부 `div`들이 옆으로 쌓이게 해줍니다.<br>
`flex`를 통해 `conA`:`conB`=2:1로 비율을 지정해줍니다.



## 3. conA 내용채우기

```html
<div class="conA">
    <!-- 하나의 게시물을 만들어줍니다. -->
    <div class="con">
        <div class="title">
            ... 프로필사진과 User이름이 들어갑니다
        </div>
        메인 이미지가 들어갑니다.
        <div class="logos">
            <div class="logos_left">
                좋아요, 댓글, 공유 logo가 들어갑니다.
            </div>
            <div class="logos_right">
                북마크 logo가 들어갑니다.
            </div>
        </div>
        <div class="content">
            좋아요 수, 댓글, 댓글 입력창이 들어갑니다.
        </div>
    </div>
</div>
```
`conA`안에 들어갈 내용들을 생각하여 `div`로 틀을 만들어 줍니다.

>title에는 프로필사진과 User이름이 들어갑니다.
```html
<div class="title">
    <img src="images/hong.png" alt="" class="img">
    <p>User name</p>
</div>
```
프로필사진의 크기를 조절하기 위해 `class="img"`를 추가합니다.

>메인 이미지를 넣어줍니다.
```html
<img src="images/picture.png" alt="" class="con_img">
```
메인 이미지의 크기를 조절하기 위해 `class=con_img"`를 추가합니다.

>각 logo들을 넣어줍니다.
```html
<div class="logos">
    <div class="logos_left">
        <img src="images/heart.svg" alt="" class="logo_img">
        <img src="images/speech-bubble.svg" alt="" class="logo_img">
        <img src="images/upload.svg" alt="" class="logo_img">
    </div>
    <div class="logos_right">
        <img src="images/bookmark.svg" alt="" class="logo_img">
    </div>
</div>
```
`div`로 오른쪽에 들어갈 logo와 왼쪽에 들어갈 logo를 지정해줍니다.<br>
각 `div`마다 이름을 정해주고,
로고 이미지의 크기를 조절하기 위해 `class=logo_img"`를 추가합니다.


>이미지 밑에 좋아요 수, 해시태그, 댓글창이 들어갑니다.
```html
<div class="content">
    <p><b>좋아요 80개</b></p>
    <p><a href="">User name</a>#해달 #html #css</p>
    <input type="text" name="" id="" value="댓글달기">
</div>
```
`<a href=""></a>`는 링크를 걸어줍니다.

### 3-1. conA css 작업하기
```css
.conA .con{
    width: 600px;
    height: 920px;
    margin-bottom: 50px;
    border: 1px solid #DBDBDB;
    border-radius: 3px;
    background-color: #ffffff;
}
.title{
    display: flex;      /*프로필사진과 User이름이 옆으로 쌓이게 하기 위함.*/
    margin: 10px;
}
.title p{
    margin: 5px 15px;
    font-size: 20px;
}
.con_img{
    width: 600px;
}
.img{
    width: 50px;
    height: 50px;
    border-radius: 50%;
}
.logos{
    display:flex;                       /*logo들이 옆으로 쌓이게 하기 위함.*/
    justify-content: space-between;     /*logos_left와 logos_right를 양끝으로 배치시킴.*/
    padding: 0 10px;
}
.content{
    padding: 10px;
}
.content input{
    width: 100%;
    height: 45px;
    border: none;
    border-top: 1px solid #DBDBDB;
    color: #999999;
    font-size: 16px;
}
.content input:focus{
    outline: none;
}
```
`input:focus`는 입력창에 클릭했을 때 파란테두리가 나타나는데 `outline: none;`을 해주면 파란테두리가 없어집니다.

![./img/ConA.PNG](./img/ConA.PNG)

이러게 나오면 ConA도 완성!!!
        
## 4. conB 내용채우기
```html
<div class="conB">
    <!-- 프로필사진과 user이름이 들어갑니다. -->
    <div class="profile">
        <img src="images/hong.png" alt="" class="img">
        <p>User name</p>
    </div>  
    <!-- Story목록이 들어갑니다. -->      
    <div class="story">
        <div class="story_title">
            <p>스토리</p>
            <p><b>모두 보기</b></p>
        </div>
        <!-- story를 업로드 한 user의 프로필 사진과 이름이 들어갑니다. -->
        <div class="story_content">
            <img src="images/hong.png" alt="" class="story_img">
            <p>User name</p>
        </div>
    </div>        
 </div>
 ```

 ### 4-1. conB css 작업하기
 ```css
.conB{
    flex: 1;
}
.profile{
    display: flex;
    margin: 10px;
}
.profile p{
    margin: 5px 15px;
    font-size: 20px;
}
.story{
    width: 250px;
    height: 170px;
    margin: 20px 5px;
    padding: 10px;
    border: 1px solid #DBDBDB;
    border-radius: 3px;
    overflow: auto;             /* div의 크기보다 내용이 더 많으면 스크롤이 생기게 해줍니다.*/
}
.story_title{
    display:flex;
    justify-content: space-between;
}
.story_title p:nth-child(1){    /*`class="story_title"`의 첫 번째 `p`를 가리킵니다.("스토리")*/
    color: #999999;
    font-size: 14px;
}
.story_title p:nth-child(2){    /*`class="story_title"`의 두 번째 `p`를 가리킵니다.("모두 보기")*/
    color: #262626;
    font-size: 12px;
}
.story_img{
    width: 40px;
    height: 40px;
    border-radius: 50%;
}
.story_content{
    display: flex;
    margin: 10px;
}
.story_content p{
    margin: 5px 15px;
    font-size: 16px;
}
 ```
 ![./img/ConB1.PNG](./img/ConB1.PNG)

축하합니다. 인스타그램 PC Version의 큰 틀은 만들었어요오!!!<br>
`conA`의 `con`게시물과 `story`의 `story_content`를 여러분이 원하시는 만큼 Ctrl+C Ctrl+V 해주세요.

```html
<div class="story">
    <div class="story_title">
        <p>스토리</p>
        <p><b>모두 보기</b></p>
    </div>
    <!-- story를 업로드 한 user의 프로필 사진과 이름이 들어갑니다. -->
    <div class="story_content">
        <img src="images/hong.png" alt="" class="story_img">
        <p>User name</p>
    </div>
    <div class="story_content">
        <img src="images/hong.png" alt="" class="story_img">
        <p>User name</p>
    </div>
    <div class="story_content">
        <img src="images/hong.png" alt="" class="story_img">
        <p>User name</p>
    </div>
    <div class="story_content">
        <img src="images/hong.png" alt="" class="story_img">
        <p>User name</p>
    </div>
</div> 
```


Story 밑에 추천 친구의 목록도 만들어 볼게요.<br>
위에 보이는 코드처럼 본인의`class="story"`를 모두 Ctrl+C 해줍니다.<br>
바로 밑에 Ctrl+V 해주세요:)<br>
`story_title`의 `p`를 `회원님을 위한 추천`으로 수정해주세요!<br>
 ![./img/ConB2.PNG](./img/ConB2.PNG)


## 5. 추가 기능 넣어보기.
> conB를 적당한 위치에 고정시켜볼 거에요. 
> 그리고 화면의 크기가 줄어들었을 때 conB의 내용을 숨겨보도록 합시다.

```css
.conB{
    flex: 1;
    position: sticky;
    top: 50px;
}
```
`conB`에 `position: sticky;`와  `top: 50px;`를 추가해줍니다.<br>
즉, 스크롤을 내리면 `conA`는 계속 내려가지만 `conB`는 위에서 50px위치에 고정되어 있습니다.<br>

```css
@media screen and (max-width: 1000px) {
    .conB{
        display: none;
    }
}
```
`style.css`의 마지막 부분에 위의 코드를 추가해줍니다.<br>
화면의 가로 비율이 1000px보다 작거나 같을 때 `conB`의 내용을 숨겨줍니다.<br><br>

이제 마지막!!!!
`html`파일의  `head>title`부분에 이미지를 추가해봅시다.
```html
<head>
    <title>instagram</title>
    <link rel="shortcut icon" href="images/instacolor.png">
    <link rel="stylesheet" href="./style.css">
</head>
```
`<link rel="shortcut icon" href="images/instacolor.png">`를 추가하면 됩니다!<br>

모두 수고하셨어요!<br>
`html` `css`에 대해 더 공부하고 싶다면 [w3school](https://www.w3schools.com/)를 추천드려요:)
