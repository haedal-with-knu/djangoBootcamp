# 장고랑 친해지자
> 장고는 파이썬을 기반으로 한 웹 프레임워크입니다.  

## 폴더 만들며 몸풀기
구름 IDE는 다들 키셨나요?  
`mysite`폴더를 하나 만들어봅시다  
```console
root@goorm:/workspace/djangoBootcamp(master)# mkdir mysite
```
`mysite`폴더로 들어가봅시다  
```console
root@goorm:/workspace/djangoBootcamp(master)# cd mysite/
```
윈도우에서 폴더 이동이랑 다르지 않습니다. 어렵지 않죠?  
아래와 같은 경로로 바뀔 겁니다
```console
root@goorm:/workspace/djangoBootcamp/mysite(master)#
```

## 개발 환경 설정

저희는 파이썬3을 사용해 공부합니다.  
구름 IDE에서 컨터이너에 설치해준 파이썬3 버전을 확인합니다
```console
root@goorm:/workspace/djangoBootcamp/mysite(master)# python3 --version
```

일반적으로 프로젝트마다 다른 버전의 라이브러리들이 필요합니다.  
이번 프로젝트에 사용할 버전의 라이브러리들을 저장할 가상환경을 설정합시다.
```console
root@goorm:/workspace/djangoBootcamp/mysite(master)# pip3 install virtualenv 
```
`myvenv`란 폴더에 가상환경을 설치합니다  
```console
root@goorm:/workspace/djangoBootcamp/mysite(master)# virtualenv myvenv
```
`/bin`,`/include`,`/lib`폴더가 설치되었는지 확인합니다.  
설치가 잘 되었나요?  

설치한 가상환경을 실행합니다
```console
root@goorm:/workspace/djangoBootcamp/mysite(master)# source myvenv/bin/activate
```
가상환경이 실행되면 cmd 창에 `(myvenv)`가 추가됩니다  
아래에서 확인해봅시다
```console
(myvenv) root@goorm:/workspace/djangoBootcamp/mysite(master)#
```
#### 드디어 장고 설치한다
```console
(myvenv) root@goorm:/workspace/djangoBootcamp/mysite(master)# pip3 install django==2.1
```
저희는 2.1 버전 장고(`django`)로 설치하였습니다  
최신 버전이면 기능이 더 많겠지만, 안정성 이슈가 있기에  
처음 배울땐 안정화가 끝난 버전을 사용하는게 좋습니다.

### 장고 프로젝트 시작하기
`djangobootcamp`란 프로젝트를 만드는 커맨드입니다.  
마지막에 점(`.`) 찍는걸 잊지 맙시다
```console
(myvenv) root@goorm:/workspace/djangoBootcamp/mysite(master)# django-admin startproject djangobootcamp .
```
장고(`django`)가 사용할 데이터베이스(`DB`)를 생성합니다(migrate 합니다)
```console
(myvenv) root@goorm:/workspace/djangoBootcamp/mysite(master)# python3 manage.py migrate
```
이제 `/mysite/djangobootcamp/settings.py`로 이동해 28번째 줄을 수정합니다
```python
ALLOWED_HOSTS = ['*']
```
### 장고 프로젝트 실행하기
```console
(myvenv) root@goorm:/workspace/djangoBootcamp/mysite(master)# python3 manage.py runserver 0:80
```
서버가 켜진다고 shell에서 말해줄텐데   
구름 ide에서 외부 `URL`로 연결하기 위해  
실행 `URL`과 `포트`를 설정해야합니다  
![img/goormideURLPort.png](img/goormideURLPort.png)  
![img/URLnPort.png](img/URLnPort.png)  

설정한 URL을 누르면  

![img/django_work_successfully.png](img/django_work_successfully.png)  

### 성공!!

