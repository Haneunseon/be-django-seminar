# 이곳에 발표자료를 구성해주세요!

- 추가적인 파일 구성은 자유롭게 해주세요.

## 1. 파이썬 가상환경 생성

- 가상환경을 생성하는 이유 
: 내가 배포하려는 서버에 내 프로젝트를 위한 패키지를 설치해주어야하는데, 필요한 패키지만 설치 하기 위해
: 버젼 충돌 이슈로 호환이 되지 않는 경우가 생기는데, 특정 프로젝트를 위한 버전의 패키지를 모아두기 위해
-> 특정 프로젝트만을 위한 패키지를 모아두기 위해

- 생성 과정
$ pip install virtualenv
: 가상환경 설치
$ virtualenv env_name
: 이름을 지정하여 가상환경 생성
$ source project_env/bin/activate
: 가상환경 활성화
<-> 가상환경 비활성화 $ deactivate
$ pip install Django
: 가상환경 내에서 장고 설치
$python -m django --version 
: 장고 설치 확인

-> 이후 디렉토리 생성 후, 프로젝트 생성
-> 디렉토리로 이동 후, $ python manage.py runserver로 장고가 잘 작동하는지 확인
-> 링크가 생성되고 접속이 되면 장고가 성공적으로 작동하는 것

$ python manage.py migrate 
: 데이터베이스 설치
: Migration은 Django가 모델(즉, 당신의 데이터베이스 스키마)의 변경사항을 디스크에 저장하는 방법

## 2. 장고의 작동 원리

![Alt text](/Users/han-eunseon/Desktop/0000.png )

- client : 웹 정보 요청 
- 최상위 conf -> url 연결 -> url pathing -> 앱의 url로 연결
- 앱 : 앱 -> view 내부로 연결 -> 내부의 index함수에서 response를 client에 전달 
- view : Template을 사용하여 클라이언트에 전송할 HTML 파일을 생성 -> response

## 3. 장고의 모델

- 모델 생성 : models.py을 수정
-> Question 과 Choice``이라는 두 가지 모델(객체 생성)

- 모델 활성화 : 객체에 접근하기 위한 Python 데이터베이스 접근 API를 생성
-> settings.py에 INSTALLED_APPS 리스트를  추가해서 polls 앱을 현재의 프로젝트에 포함 

- polls 앱 내에 migrations 디렉토리 생성 
$ python manage.py makemigrations polls
: Migration은 Django가 모델(즉, 당신의 데이터베이스 스키마)의 변경사항을 디스크에 저장하는 방법
-> migration내에 0001_initial.py파일 생성
-> 0001_initial.py파일에 데이터 베이스의 테이블을 만들기위한 설계도가 생성됨

- 테이블 생성
$ python manage.py migrate
-> 모델이 수정되었을 때는 python manage.$ py makemigrations을 통해 이 변경사항에 대한 마이그레이션 생성 후, $ python manage.py migrate 명령을 통해 변경사항을 데이터베이스에 적용

## 4. API 

- API : 개발자가 필요로 하는 데이터를 뽑아낼 수 있도록 만들어놓은 함수, 즉 서버(데이터베이스)에게 데이터를 입력할 수 있도록 만들어놓은 함수

- python 쉘 실행후, 작업 진행
 
## 5. admin

- 관리자 사이트에 로그인하기 위한 유저를 생성
- polls/admin.py 파일 수정 -> 사이트에서 poll 앱 수정 가능하게 함