# TIL 7.7

Prefetch()

- ORM JOIN을 하고 싶을 때 N:1 , N:N 의 관계일 경우 prefetched_related()를 사용합니다.
- selected_related와 달리 prefetch_related는 SQL의 JOIN을 실행하지 않고, python에서 joining을 실행
- prefetch() 객체는 prefetch_related()를 컨트롤할 때 사용한다. (lookup, queryset=None, to_attr=None)
- ex) prefetch_related( 'allergy' ).filter( name = '아이스' ) → allergy table을 일단 캐시데이터로 가져와 저장, 이름이 아이스인 객체를 가져옴

Primary key & Foreign key

- Primary : Data table에 있는 유일하게 구분되는 Data key, 유일한 값이며 공백 X
- Foreign : 한 table에 참조되는 다른 table 간의 연결되는 primary key column이 foreign key, 다른 primary key를 참조하는 속성 또는 집합을 의미합니다.

import Q

- WHERE 절에 OR문을 추가하고 싶다면 Q()를 사용.     ~ Q() :  NOT 구문

annotate()

- Django에서는 주석 대신 '필드를 추가한다고 생각
- 필드 하나를 만들고 거기에 '어떤 내용'을 채우게 만드는 것

—> SQL의 GROUP BY와 같은 의미

get_queryset VS queryset

- get_q : request마다 query를 발생시킵니다. ( 조건이 걸린 queryset을 쓸때는 get_queryset()을 오버라이딩하자.)
- queryset : request 발생 시 한번만 쿼리셋이 동작

오버로딩 & 오버라이딩

- 오버로딩 : 같은 이름의 메소드 여러개를 가지면서 매개변수의 유형과 개수를 다르도록 하는 기술
- 오버라이딩 : 상위 클래스가 가지고 있는 메소드를 하위 클래스가 재정의해서 사용