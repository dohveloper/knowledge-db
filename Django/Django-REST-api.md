# Django REST Framework

## 💡 1.Django REST Framework 란? 

Django REST Framework란 기존의 Django의 모델을 강력한 REST API로 바꿀수 있도록 도와주는 오픈소스 라이브러리이다.
기존의 Django에서는 ORM을 통해 데이터베이스의 자료에 접근하기 때문에 json 형태를 이용하는 REST api를 사용하기 위해서는 변환이 필요하다. 
Django REST Framework는 serializer를 제공함으로써 쉽게 json으로 Django DB에 접근할 수 있도록 도와준다. 


## 🛤️ 2.Django와 React를 같이 쓰기 위한 방법은?

- 1) React, Django 각각 따로
- 2) Django 프로젝트에 React.js 빌드 코드를 임베드
- 3) Django 프로젝트에 Template에 React를 각각 임베드

각각의 장 단점이 있으나 2번의 방법이 비교적 제일 간단해보인다.


## 💬 3.Django REST Framework의 주요 개념들
### 1) Model 
사용할 DB의 모델을 만든다 (Django와 다를 바 없음)

###2) Serializer 
DRF 공식문서에 따르면 시리얼라이저란 쿼리셋이나 모델인스턴스와 같은 복잡한 데이터를 json 등과 같은 컨텐트 타입으로 쉽게 변환할 수 있는 파이썬 데이터타입으로 만들어주는 것이라고 한다.
>Serializers allow complex data such as querysets and model instances to be converted to native Python datatypes that can then be easily rendered into JSON, XML or other content types.
DRF사용을 위해서는 시리얼라이저를 사용할 모델을 연결해주어야한다.
```
# serializers.py
from rest_framework import serializers

from .models import Item

class ItemSerializer(serializers.HyperlinkedModelSerializer):
    class Meta:
        model = Item
        fields = ('name', 'alias')
```

### 3) View
Django 공식문서에 따르면 뷰란 특정 템플릿과 함수를 전달하는 "일종의" 장고앱의 웹페이지라고 한다. 
이것만으로는 살짝 설명이 모호하다. 
사실 더 도움이 되는건 문서 나중 부분에 있는 다음과 같은 설명이다
"각 뷰는 두 가지 일을 담당한다: 요청한 페이지의 HttpResponse를 반환하거나 Http404 같은 예외 반환"
>Each view is responsible for doing one of two things: returning an HttpResponse object containing the content for the requested page, or raising an exception such as Http404. The rest is up to you.

즉 간단히 말해서 요청한 페이지를 "자 여기있어" 하는 역할을 하는 것이다.
DRF에서는 "요청한 페이지" 대신에 요청한 json이 되시겠다. 

```
from rest_framework import viewsets

from .serializers import ItemSerializer
from .models import Hero


class ItemViewSet(viewsets.ModelViewSet):
    queryset = Item.objects.all().order_by('name')
    serializer_class = ItemSerializer
```


### 4) URL 
이 부분도 기존 Django의 방식과 크게 다르지 않다.


참고자료:
- https://www.caktusgroup.com/blog/2018/02/26/basics-django-rest-framework/
- https://www.valentinog.com/blog/drf/#setting-up-the-controll-ehm-the-views
- https://medium.com/swlh/build-your-first-rest-api-with-django-rest-framework-e394e39a482c