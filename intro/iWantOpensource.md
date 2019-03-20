# 저도 오픈소스 프로젝트 진행하고 싶습니다
### 프로그래밍이 처음이신 분들은 이번 장은 패스

Github에서 사용하는 문서는 마크다운을 사용합니다  
마크다운을 활용해 오픈소스 문서를 작성하는 방법을 공부합니다.

가볍게 훑어봅시다. [Github 마크다운 작성법](https://gist.github.com/ihoneymon/652be052a0727ad59601)

### 코드를 세상에 보이자
코드를 전부 작성한 후   
Github에 업로드를 해야합니다  
프로젝트의 제일 상위 폴더로 이동 후 아래의 명령어를 입력합니다.  

* Git 초기화
```console
$ git init
```
* 모든 파일을 Git 저장소에 추가
```console
$ git add .
```
* Git Commit
```console
$ git commit -m "이번에 코드를 업로드하는지 코멘트"
```
* Git 저장소 설정
```console
$ git remote add origin 레포지토리URL
```
* Git Push
```console
$ git push origin master
```

기본적으로 사용하는 명령어들입니다.  
추가적인게 필요할땐 Git에서 설명을 해줍니다.  
가이드를 따릅시다  

## 다음 강의는
### [1. 장고랑 친해지자](https://github.com/haedal-with-knu/djangoBootcamp/blob/master/tutorials.md)  