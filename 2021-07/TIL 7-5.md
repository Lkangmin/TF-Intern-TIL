# TIL

가상환경 (test 하기)

- pipenv shell
- python [manage.py](http://manage.py) runserver —> api 찾은 후 test
<br/><br/>

디버깅

- bug&play  아이콘 클릭 → 초록색 play 아이콘 실행
- 원하는 포인트에 break point를 설정하고 테스트를 해보자!
- F10 → 한줄씩 디버깅
<br/><br/>

Test 방법

- python [manage.py](http://manage.py) test app 이름/tests.py
- python manage.py test <app 이름>.<test 파일>.<class 이름>.<method 이름>
<br/><br/>

스테이징 서버 (staging server)

- 실제 운영 환경과 거의 동일한 환경으로 만들어놓고 기능을 검증하는 환경
<br/><br/>

Migrate(django)

- 모델에서 변수가 추가되거나 삭제되었을 때 내용이 바뀌었거나 같은 경우에 사용. 즉, 모델이 db의 테이블이라고 생각
- python manage.py makemigrations <app-name>  (마이그레이션 파일 생성) —> 초안 생성
- python manage.py makemigrations —empty <app-name>  (빈 migration 파일 생성)/
- python manage.py  migrate <app-name>  (마이그레이션 적용)
- python manage.py showmigrations, sqlmigrate (마이그레이션 적용 현황, SQL 내역) 
  <br/><br/>
  
git branch 삭제
- git branch -d <이름>
<br/><br/>
  

가상환경 파이썬 업데이트
- pipenv --python <새 버전>
  (해당 파이썬 버전은 깔려있어야 한다!)
<br/><br/>
  
git stash
- 수정된 내용을 보관하는 용도
- add 한 항목을 stash 후에 다시 불러오면 add가 풀려있다!
- https://gmlwjd9405.github.io/2018/05/18/git-stash.html
<br/><br/>
  

postgreSQL DB 생성 (mac)
- 설치 			 brew install postgresql
- 서비스 시작  brew services start postgresql
- 접속   		 psql postgres
- DB list	 	\list  
- 사용자 list	\du
- DB 생성 		CREATE DATABASE test;     —> 무조건 세미콜론!!
- DB 소유자 변경	ALTER DATABASE 디비명 OWNER TO 계정명
- DB 접근 \c DB이름
  
  
