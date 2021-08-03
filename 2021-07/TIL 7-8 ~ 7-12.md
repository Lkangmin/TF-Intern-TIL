# TIL 7.8~7.12

group_concat

- 컬럼값들을 하나의 값으로 합치는 역할을 한다.
- mysql : GROUP_CONCAT()
- Postgresql : STRING_AGG()
<br><br>


재귀 query

- with recursive CTE as (~~
<br><br>


Pagination

- 백엔드에서 가지고 있는 데이터는 많고, 그 데이터를 한 화면에 전부 보여줄 수 없는 경우에 사용한다. 일정 길이로 끊어서 전달한다.
- ex) 흔히 게시판의 "이전/다음 페이지"를 끊어 보여주는 기능
- 프론트 엔드 : 현재의 위치(offset)과 추가로 보여줄 컨텐츠의 수(limit)을 백엔드로 전달
<br><br>


LimitOffsetPagination

- offset : 몇 번째 레코드로부터 보여줄지 설정, 설정하지 않을 시 첫 번째 레코드부터 보여줌
- limit : 몇 개의 레코드를 보여줄지 설정

 —> offset번째 레코드부터 offset+limit-1 번째 레코드까지 보여준다.
<br><br>


APIClient()

- API 통신을 하기 위해서 rest_framework.test의 APIClient()모듈을 써야 한다. 해당 모듈엔 http의 메소드가 정의 되어 있으며, 사용에 맞는 함수를 호출하면 된다.
<br><br>


JOIN

- 둘 이상의 테이블을 연결해서 데이터를 검색하는 방법
- Inner : 교집합, 공통적인 부분
- LEFT : 왼쪽에 있는 거 전부
- LEFT OUTER : 왼쪽에 있는 것만
- RIGHT, RIGHT OUTER
- OUTER : 합칩합, 전부
- FULL OUTER : 차집합의 합, 왼쪽에 있는 거 + 오른쪽에 있는 거
<br><br>


SQL 반복문

- Mysql : start with~
- Postgresql : with recursive as~ (재귀랑 중복??)
<br><br>


to_timestamp

- Postgresql에서 사용하는 date 함수
- to_timestamp(~,'YYYY-MM-DD HH24:MI:SS')
<br><br>


OVER 

ORDER BY, GROUP BY 서브쿼리를 개선하기 위해 나온 함수
<br><br>


time slot 만들기

- Postgresql : generate_series
<br><br>


extract

- 원하는 것만 추출
- ex) 날짜 데이터에서 시간만 추출
