# TIL 7.7

prefetch_related

- select_related, prefetch_related —> 하나의 Queryset을 가져올 때, 미리 관련된 object들까지 모두 다 불러와주는 함수이다.
- ORM JOIN을 하고 싶을 때 N:1 , N:N 의 관계일 경우 prefetched_related()를 사용합니다.
-> 역참조일때는 prefetch_related를 사용한다! (그래서 DB hit 두번!)
- selected_related와 달리 prefetch_related는 SQL의 JOIN을 실행하지 않고, python에서 joining을 실행
- Prefetch() 객체는 prefetch_related()를 컨트롤할 때 사용한다. (lookup, queryset=None, to_attr=None)
- ex) prefetch_related( 'allergy' ).filter( name = '아이스' ) → allergy table을 일단 캐시데이터로 가져와 저장, 이름이 아이스인 객체를 가져옴
<br/><br/>


Prefetch 객체 사용법
![Pasted Graphic 1](https://user-images.githubusercontent.com/31716984/144387888-f213ef03-a8d0-4537-9236-1463c1e60037.png)<br/>
- lookup 설정 :  같이 가져오려는 테이블 (보통 역참조 관계를 가져오므로 테이블명_set)
- queryset 설정 : 관련 테이블에서 가져오려는 쿼리셋 설정
- to_attr 설정 : to_attr 인수를 이용해 prefetch에 독자적인 속성을 부여 가능 (class내에 새로운 변수로 설정)
- https://docs.djangoproject.com/en/3.2/ref/models/querysets/#django.db.models.Prefetch
<br/><br/>


Primary key & Foreign key

- Primary : Data table에 있는 유일하게 구분되는 Data key, 유일한 값이며 공백 X
- Foreign : 한 table에 참조되는 다른 table 간의 연결되는 primary key column이 foreign key, 다른 primary key를 참조하는 속성 또는 집합을 의미합니다.
<br/><br/>


import Q

- WHERE 절에 OR문을 추가하고 싶다면 Q()를 사용.     ~ Q() :  NOT 구문
<br/><br/>


annotate()

- Django에서는 주석 대신 '필드를 추가한다고 생각
- 필드 하나를 만들고 거기에 '어떤 내용'을 채우게 만드는 것
—> SQL의 GROUP BY와 같은 의미
<br/><br/>


get_queryset VS queryset

- get_q : request마다 query를 발생시킵니다. ( 조건이 걸린 queryset을 쓸때는 get_queryset()을 오버라이딩하자.)
- queryset : request 발생 시 한번만 쿼리셋이 동작
<br/><br/>


오버로딩 & 오버라이딩

- 오버로딩 : 같은 이름의 메소드 여러개를 가지면서 매개변수의 유형과 개수를 다르도록 하는 기술
- 오버라이딩 : 상위 클래스가 가지고 있는 메소드를 하위 클래스가 재정의해서 사용
