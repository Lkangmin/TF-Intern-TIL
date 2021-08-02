# TIL 7.26 ~ 7.30

TimeStampedModel

- django에서 model에 데이터 생성 시간, 업데이트 시간을 기록하기 위해 create_time, modified_time 필드를 설정해주는 경우가 자주 있다. 이 필드들은 많은 모델에서 사용되는 필드이므로 TimeStampedModel에 한 번만 필드를 지정해놓고 상속을 받아서 사용하는 것이 좋다. 일일이 두 가지 필드를 해당 모델들에 추가할 필요가 없고, 추가하지 않아서 발생하는 문제들을 방지할 수 있는 장점이 있다.

—> create_time, modified_time 필드를 따로 지정하지 않아도 TimeStampedModel을 상속 받았기 때문에 데이터가 생성될 때, 수정될 때의 시간이 기록된다.

<br>

class Meta

- 권한, 데이터베이스 이름, 단 복수 이름, 추상화, 순서 지정 등과 같은 모델에 대한 다양한 사항을 정의하는 데 사용한다.

<br>
Abstract base 상속

- Meta 클래스에서 abstract = true 로 설정하면 부모 모델은 실제로 또는 물리적으로 존재하지 않는 가상의 클래스가 된다. 자식 모델들은 부모의 필드와 속성, 함수들을 다 물려받아 실체가 있는 DB 테이블이 된다. 즉, abstract base를 사용한다는 것은 자식 모델들이 부모 없이 각각 독립적인 DB 테이블로 존재하며, 자식과 부모의 상속 관계는 실제로 없는 것이다.

<br>
Django 유저 모델

- Proxy model : 기존의 유저 모델을 그대로 사용하되, 일부 동작을 변경하는데만 사용
- User Profile : 하나의 새로운 모델을 정의한 후, 유저 모델과 1:1 관계설정 (프로필 모델 참조)
- AbstractBaseUser : 완전한 새로운 유저 모델을 만들 때 사용
- AbstractUser : 기존의 유저 모델을 사용하되, 추가적인 정보를 더 넣고 싶을 때 사용, 2번 방법은 추가로 클래스를 생성하지만, 이 방법의 경우 추가로 클래스를 생성하지 않음.

<br>
UUID

- 기본적으로 어떤 데이터를 고유하게 식별하는 데 사용되는 16바이트(128비트) 길이의 숫자입니다. 이 숫자는 32개의 16진수로 구성되며, 5개의 그룹으로 표시되고 각 그룹은 하이픈으로 구분된다.

—> uuid.uuid4() : 버전 4 uuid를 생성하는 함수

<br>
validators.UnicodeUsernameValidator

- 유니 코드 문자를 허용하는 필드 유효성 검사기 @, +, ., -와 _에 대한 기본 유효성 검사기입니다.

<br>
hasattr(object, name)

- object의 속성 존재를 확인한다. 만약 argument로 넘겨준 object에 name의 속성이 존재하면 True, 아니면 False를 반환한다.

<br>
gettext_lazy()

- 다국어 지원을 위해 사용한다. _로 사용

<br>
swappable = 'AUTH_USER_MODEL'

- AUTH_USER_MODEL이라는 속성에 의해서 무엇인가가 바뀔 수 있다는 것을 의미합니다.

<br>
textchoices(integer choices 등등), choices

- charfield는 길이만 맞으면 모든 텍스트가 저장이 가능한데 choice를 이용하여 우리가 저장하고 싶은 종류의 텍스트만 저장하게 만듭니다.

<br>
Multi-table inheritance

- 상속을 하나 거칠때마다 테이블이 하나씩 더 생긴다. 여러개의 테이블을 사용해서 상속을 구현한 것으로 계층 구조의 각 모델이 모두 각각 자신을 나타내는 모델일 때를 말한다. 이는 즉 부모클래스, 자식클래스도 모두 데이터베이스 테이ㅣ블로 나타난다는 것을 의미한다.

—> 상속받은 자식은 부모 모델명_ptr_id (연결을 위해 존재?)

<br>
AbstractBaseModel

- is_active (bool) 항목을 가지고 있습니다. 또한, TimeStampModel을 상속받고 있어 create, modified time 항목도 가지고 있습니다.

<br>
<Django 기본적인 필드 타입들>

![Untitled 1](https://user-images.githubusercontent.com/31716984/127894686-07a5fdb6-b66c-4de8-9126-0bf59b5864c6.png)

- 옵션들

![Untitled 2](https://user-images.githubusercontent.com/31716984/127894732-032406f9-7454-476f-b77b-321d8c19d3f3.png)

ref

1.[https://nachwon.github.io/django-field/](https://nachwon.github.io/django-field/)

2.[http://pythonstudy.xyz/python/article/308-Django-%EB%AA%A8%EB%8D%B8-Model](http://pythonstudy.xyz/python/article/308-Django-%EB%AA%A8%EB%8D%B8-Model)


<br>
역참조, 역관계란? (Reverse relationships)

- 데이터베이스 테이블에서 Foreign Key가 없고 다른 테이블의 Foreign key로 지정된 테이블일 때, 나를 참조하는 테이블에 접근하는 것 (부모가 자식 클래스 접근 느낌??)
- OneToOneField : 하나의 객체를 반환 (1:1 의 관계)
- ForeignKey : Query set을 반환 —> _set을 이용해서 역참조 (1:N의 관계), ManyToMany도 _set을 사용


<br>
일반 토큰 기반의 인증과 클레임 (claim) 토큰 기반 인증

- 토큰 → 인증을 위해 사용
- 일반 토큰 : random  string 기반으로 구성
- 클레임 : 사용자 정보나 데이터 속성 등을 의미한다. 클래스 토큰이라 하면 토큰 안에 저런 정보를 담고 있는 토큰이다. 대표적인 것이 JWT이다.


<br>
JWT 인증 (Json Web Token)

- Built-in Token : 하나의 토큰으로 모든 세션을 관리, time stamp가 없기 때문에 custom 하거나 DB에서 삭제하지 않는 이상 영구적
- JWT : 세션 하나에 토큰 하나가 발급되며,  time stamp가 있어 영구적이지 않고 언젠가 만료
- JWT : 헤더(header), 페이로드(payload), 서명(signature)의 세가지로 나눠져 있다.
- ref

https://elfinlas.github.io/2018/08/12/whatisjwt-01/

[https://django-rest-framework-simplejwt.readthedocs.io/en/latest/](https://django-rest-framework-simplejwt.readthedocs.io/en/latest/)


<br>
try / except, raise

- 예외처리
- raise : 사용자가 직접 에러를 발생시키는 기능


<br>
메서드

- instance, static, class method가 존재
- instance : 클래스 내에 있는 평소에 쓰는 내장함수(?), 첫번째 파라미터는 항상   self
- static : self 파라미터가 없고 인스턴스 변수에 접근 X, 객체 필드와 독립적이지만 로직상 클래스내에 포함되는 메서드
- class : static과 비슷, 객체 인스턴스를 의미하는  self  대신 cls라는 클래스를 의미하는 파라미터 존재,  cls를 통해 클래스 변수 접근 가능 (인스턴스 변수 X)
- 인스턴스 변수 : 하나의 클래스를 이용해 여러개의 객테 인스턴스를 생성하여 사용 가능, 클래스 변수는 하나의 클래스에 하나, 인스턴스는 각 객체 인스턴스마다 별도로 존재, 메서드 안에서 사용
- 클래스 변수 : 메서드 밖에 존재하는 변수, 해당 클래스를 사용하는 모두에게 공용으로 사용되는 변수

<br>
factory.fuzzy.FuzzyChoice()

- fuzzy는 Faker로 대체되어 많이 쓰지 않음, fuzzychoice는 choicefield에 대응하는 역할

<br>
facotry.lazy_attribute

- 일부 속성은 인스턴스가 생성될 때마다 할당된 값이 필요

<br>
django permissions

- django에서 기본적인 권한을 제공합니다.

![Untitled 3](https://user-images.githubusercontent.com/31716984/127894868-eaa97fbf-9f3a-4da1-b27a-a13071cbe737.png)

![Untitled](https://user-images.githubusercontent.com/31716984/127894886-39d17407-a66a-41eb-8013-d7e373403b9d.png)


- Tip ) DRF = Django REST Framework
- ref ) [https://ssungkang.tistory.com/entry/Django-Authentication-과-Permissions](https://ssungkang.tistory.com/entry/Django-Authentication-%EA%B3%BC-Permissions)

<br>
 커스텀 Permission

- has_permission (request, view) : 뷰 호출 접근 권한, APIView 접근 시 체크
- has_object (request, view, obj) : 개별 레코드 접근 권한, APIView의 get_object 함수를 통해 object 획득 시 체크, 브라우저를 통한 API 접근시에 CREATE/UPDATE Form 노출 여부 확인 시에
- Request.user.is_authenticated —> 해당 유저가 로그인되어 있을 경우

<br>
super()

- 자식 클래스에서 부모 클래스의 내용을 사용하고 싶을 경우 사용

<br>
serializer

- 쿼리셋, 모델 인스턴스 —> 파이썬 데이터 타입으로 변환
- meta에 원형 모델을 쓰고, 사용할 field를 쓰는 형식으로 매우 간단하게 코드 작성 가능
- create, update 함수 등은 오버라이딩 하여 사용가능
- [https://velog.io/@jcinsh/DRF-14-DRF-공식문서-요약](https://velog.io/@jcinsh/DRF-14-DRF-%EA%B3%B5%EC%8B%9D%EB%AC%B8%EC%84%9C-%EC%9A%94%EC%95%BD)

<br>
orderDict()

- 기본 dict와 거의 비슷하지만, 입력된 아이템들의 순서를 기억하는 dict 클라스이다.

<br>
Refresh token

- JWT 방식의 문제로 토큰을 탈취 당할 경우 보안에 취약하다는 점입니다. 유효기간이 짧은 경우, 사용자는 새 토큰을 발급받기 위해 로그인을 자주 시도해야 하고 유효기간을 늘리면 탈취 당했을 때 보안에 취약해지게 됩니다.

—> 유효기간을 짧게 하면서 보안을 챙길 수 있는 방식이 refresh token

<br>
Mixin

- 클래스에 부가적인 기능이나 정보를 추가해주기 위한 모듈
