# Swagger

## Swagger란 
Swagger란 REST API를 설계하고 아름답고 접근하기 쉽게 문서화할 수 있도록 도와주는 툴이다

>
>Swagger allows you to describe the structure of your APIs so that machines can read them. 
>.........(중략)...........
>Why is it so great? Well, by reading your API’s structure, we can automatically build beautiful and interactive API documentation.
>
>출처: https://swagger.io/docs/specification/2-0/what-is-swagger/
>

## 💻 Swagger 문서는 어떤 세가지 요소로 나눌 수 있는가?
- `API 문서 관련 부분`
- `엔드포인트`
- `스키마`

## 📄 공식 문서는 어떤 7가지 요소로 나누어져있는가?
- `openapi`: 버전
- `info`: 프로젝트 정보라고 생각하면 되겠다. 문서정보와 관련된 정보들이 있다.
- `servers`: Swagger에서는 API를 직접 테스트도 할 수 있는데 이와 관련된 정보를 입력한다.
- `tags`: 카테고리라고 생각하면 된다.
- `paths`: 문서의 핵심이 되는 API endpoint 들에 대한 상세한 정보가 담기는 부분이다.
- `externalDocs`: 외부링크 및 문서( 프로젝트 설명본문 하단에 나온다.)
- `components`: 그외 기타 설정들

## 🌐 엔드포인트 파트는 어떤 요소로 나눌 수 있는가?
- 엔드포인트
- `parameter`
- `request body`
- `responses`













