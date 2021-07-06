# TIL

Serializer

- django 어플리케이션은 API를 요청한 어플리케이션과 JSON 데이터를 주고 받을 수 있어야 합니다. 이를 위해서 DB 인스턴스를  JSON 데이터로 Serializer하거나, 반대로 JSON 데이터를 DB 인스턴스로 다시 
<br/>

Serializer할 수 있어야 합니다.

—> 이러한 목적으로  Django REST framework가 제공하는 class가 Serializer
<br/>

SerializerMethodField

- 모델에 없는 필드를 추가하고 싶거나 모델에 있는 값을 변형해서 새로운 필드의 값으로 넣고 싶을 때 사용
<br/>

RequestFactory class

- 테스트 클라이언트와 동일한 API를 공유합니다. 테스트 클라이언트 API의 약간 제한된 하위 집합입니다.

—> APIRequestFactory : 기존 class 확장
<br/>

 force_authenticate()

- 강제 요청, RequestFactory를 사용하여 직접 뷰를 테스트할 때는 인증자격 증명을 작성하지 않고 직접 자격요청을 인증하는 것이 편리합니다.
<br/>

URL Reverse

- View 함수를 사용하여 URL을 역으로 계산하는 것

—> 개발자가 일일이 URL을 외워 하드코딩하지 않아도 됩니다

—> URL이 변경되어도, URL Reverse가 변경된 URL을 추적합니다.

—> [urls.py](http://urls.py)에서 정의한 url pattern의 name만 알고 있다면 view 함수를 통해 매칭되는 url을 찾아 이를 전달받을 수 있습니다.
<br/>

ORM 서비스

- 객체와 관계와의 설정,      관계 : 관계형  DB
- 객체 생성

    fb = Object_name(~~)

- 새 객체 INSERT

    Fb.save()

    —> SQL의 INSERT가 생성되고 실행되어 테이블에 데이터가 추가됩니다.

-tip) Django는 디폴트로 모든 Django 모델 클라스에 대해 object라는 Manager 객체를 자동 추가 (데이터를 읽어오기 위해서 사용) —> 모델 클라스_이름.objects

- all()

    테이블 데이터를 전부 가져오기 위해서 사용

- get()

    하나의 row만을 가져오기 위해서 사용

- filter()

    특정 조건에 맞는 row들을 가져오기 위해서 사용    ex) filter( name = 'Kim' )

- exclude()

    특정 조건을 제외한 나머지 row들을 가져오기 위해서 사용

- count()

    데이터의 개수 (row 수)를 세기 위해서 사용

- order_by()

    데이터를 키에 따라 정렬하기 위해서 사용, 앞에 -가 붙으면 내림차순

    ex) order_by( 'id', '-createData' )  → id을 기준으로 올림차순, createData를 기준으로 내림차순으로 정렬

- distinct

    중복된 값은 하나로만 표시하기 위해 사용

- first()

    데이터들 중 처음에 있는 row만을 리턴

- last()

    데이터들 중 마지막에 있는 row만을 리턴  ( order_by 후에 하면, 해당 필드 정렬했을 때 마지막 row 리턴)

- delete()

    데이터를 삭제하기 위해서 먼저 삭제할 row 객체를 얻은 후 delete() 호출
<br/>

Selected related

- SQL 문의 JOIN을 사용하여 Query set을 가져올 때, 미리 related object까지 불러오는 함수 (DB 접근 빈도를 낮춰줍니다)
<br/>

Prefetch related

- Selected related와 같이 data를 cache에 저장하며, 모든 relationships가 가능

      (many to many 관계를 대상으로 참조할 때 사용 권장)
<br/>


import F

- F(name) → F() 객체는 모델 필드의 값을 나타냅니다. 데이터베이스에서 파이썬 메모리로 데이터를 가져오지 않고 모델 필드 값을 참조하고 사용하여 데이터베이스 작업을 수행할 수 있습니다. 대신  Django는 F() 객체를 사용하여 데이터베이스 수준에서 필요한 작업을 설명하는 SQL 표현식을 생성합니다.
