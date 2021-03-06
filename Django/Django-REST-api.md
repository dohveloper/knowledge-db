# Django REST Framework

## ๐ก 1.Django REST Framework ๋? 

Django REST Framework๋ ๊ธฐ์กด์ Django์ ๋ชจ๋ธ์ ๊ฐ๋ ฅํ REST API๋ก ๋ฐ๊ฟ์ ์๋๋ก ๋์์ฃผ๋ ์คํ์์ค ๋ผ์ด๋ธ๋ฌ๋ฆฌ์ด๋ค.
๊ธฐ์กด์ Django์์๋ ORM์ ํตํด ๋ฐ์ดํฐ๋ฒ ์ด์ค์ ์๋ฃ์ ์ ๊ทผํ๊ธฐ ๋๋ฌธ์ json ํํ๋ฅผ ์ด์ฉํ๋ REST api๋ฅผ ์ฌ์ฉํ๊ธฐ ์ํด์๋ ๋ณํ์ด ํ์ํ๋ค. 
Django REST Framework๋ serializer๋ฅผ ์ ๊ณตํจ์ผ๋ก์จ ์ฝ๊ฒ json์ผ๋ก Django DB์ ์ ๊ทผํ  ์ ์๋๋ก ๋์์ค๋ค. 


## ๐ค๏ธ 2.Django์ React๋ฅผ ๊ฐ์ด ์ฐ๊ธฐ ์ํ ๋ฐฉ๋ฒ์?

- 1) React, Django ๊ฐ๊ฐ ๋ฐ๋ก
- 2) Django ํ๋ก์ ํธ์ React.js ๋น๋ ์ฝ๋๋ฅผ ์๋ฒ ๋
- 3) Django ํ๋ก์ ํธ์ Template์ React๋ฅผ ๊ฐ๊ฐ ์๋ฒ ๋

๊ฐ๊ฐ์ ์ฅ ๋จ์ ์ด ์์ผ๋ 2๋ฒ์ ๋ฐฉ๋ฒ์ด ๋น๊ต์  ์ ์ผ ๊ฐ๋จํด๋ณด์ธ๋ค.


## ๐ฌ 3.Django REST Framework์ ์ฃผ์ ๊ฐ๋๋ค
### 1) Model 
์ฌ์ฉํ  DB์ ๋ชจ๋ธ์ ๋ง๋ ๋ค (Django์ ๋ค๋ฅผ ๋ฐ ์์)

###2) Serializer 
DRF ๊ณต์๋ฌธ์์ ๋ฐ๋ฅด๋ฉด ์๋ฆฌ์ผ๋ผ์ด์ ๋ ์ฟผ๋ฆฌ์์ด๋ ๋ชจ๋ธ์ธ์คํด์ค์ ๊ฐ์ ๋ณต์กํ ๋ฐ์ดํฐ๋ฅผ json ๋ฑ๊ณผ ๊ฐ์ ์ปจํํธ ํ์์ผ๋ก ์ฝ๊ฒ ๋ณํํ  ์ ์๋ ํ์ด์ฌ ๋ฐ์ดํฐํ์์ผ๋ก ๋ง๋ค์ด์ฃผ๋ ๊ฒ์ด๋ผ๊ณ  ํ๋ค.
>Serializers allow complex data such as querysets and model instances to be converted to native Python datatypes that can then be easily rendered into JSON, XML or other content types.
DRF์ฌ์ฉ์ ์ํด์๋ ์๋ฆฌ์ผ๋ผ์ด์ ๋ฅผ ์ฌ์ฉํ  ๋ชจ๋ธ์ ์ฐ๊ฒฐํด์ฃผ์ด์ผํ๋ค.
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
Django ๊ณต์๋ฌธ์์ ๋ฐ๋ฅด๋ฉด ๋ทฐ๋ ํน์  ํํ๋ฆฟ๊ณผ ํจ์๋ฅผ ์ ๋ฌํ๋ "์ผ์ข์" ์ฅ๊ณ ์ฑ์ ์นํ์ด์ง๋ผ๊ณ  ํ๋ค. 
์ด๊ฒ๋ง์ผ๋ก๋ ์ด์ง ์ค๋ช์ด ๋ชจํธํ๋ค. 
์ฌ์ค ๋ ๋์์ด ๋๋๊ฑด ๋ฌธ์ ๋์ค ๋ถ๋ถ์ ์๋ ๋ค์๊ณผ ๊ฐ์ ์ค๋ช์ด๋ค
"๊ฐ ๋ทฐ๋ ๋ ๊ฐ์ง ์ผ์ ๋ด๋นํ๋ค: ์์ฒญํ ํ์ด์ง์ HttpResponse๋ฅผ ๋ฐํํ๊ฑฐ๋ Http404 ๊ฐ์ ์์ธ ๋ฐํ"
>Each view is responsible for doing one of two things: returning an HttpResponse object containing the content for the requested page, or raising an exception such as Http404. The rest is up to you.

์ฆ ๊ฐ๋จํ ๋งํด์ ์์ฒญํ ํ์ด์ง๋ฅผ "์ ์ฌ๊ธฐ์์ด" ํ๋ ์ญํ ์ ํ๋ ๊ฒ์ด๋ค.
DRF์์๋ "์์ฒญํ ํ์ด์ง" ๋์ ์ ์์ฒญํ json์ด ๋์๊ฒ ๋ค. 

```
from rest_framework import viewsets

from .serializers import ItemSerializer
from .models import Hero


class ItemViewSet(viewsets.ModelViewSet):
    queryset = Item.objects.all().order_by('name')
    serializer_class = ItemSerializer
```


### 4) URL 
์ด ๋ถ๋ถ๋ ๊ธฐ์กด Django์ ๋ฐฉ์๊ณผ ํฌ๊ฒ ๋ค๋ฅด์ง ์๋ค.


์ฐธ๊ณ ์๋ฃ:
- https://www.caktusgroup.com/blog/2018/02/26/basics-django-rest-framework/
- https://www.valentinog.com/blog/drf/#setting-up-the-controll-ehm-the-views
- https://medium.com/swlh/build-your-first-rest-api-with-django-rest-framework-e394e39a482c