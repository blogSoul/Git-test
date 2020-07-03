## 😎DJANGO_HARD😎

사용자는 request를 보내고 django reset framework는 JSON object를 보냅니다.
JSON : JavaScript Object Notation
Ex)
```
import json

diary = {
    'id': 3 ,
}

print(diary)
diary_s = json.dumps(diary) #dumps : dictionary -->json
print(diary_s)
diary_back = json.loads(diary_s) #loads : json --> dictionary
print(diary_back)
```

## 😎http request & response😎

get : 갖다줘 
post : 처리해줘
put : 요청된 자원을 수정합니다.
delete : 요청된 자원을 삭제합니다.
patch : 요청된 자워의 일부를 교체합니다.
option : 웹 서버에서 지원되는 메소드의 종류 확인

response 종류
1xx(정보): 요청을 받았으며 프로세스를 계속한다.
2xx(성공): 요청을 성공적으로 받았으며 인식했고 수용하였다.
3xx(리다이렉션): 요청 완료를 위해 추가 작업 조치가 필요하다.
4xx(클라이언트 오류): 요청의 문법이 잘못되었거나 요청을 처리할 수 없다.
5xx(서버 오류): 서버가 명백히 유효한 요청에 대한 충족을 실패했다.

## 😎Httpie😎

pip install --upgrade httpie : 패키지 설치
httpie 명령어 : http [flags][METHOD] URL [ITEM [ITEM]]
GET는 == 로 PUT은 = 로 설정합니다.

Ex)
http get "example.com"
http --headers "example.org"
http --form post "http://127.0.0.1:8000/classcrud/newblog" title="new title" body="new body" -->csrf 정책 오류가 나올수도...
http delete "http://127.0.0.1:8000/classcrud/newblog" -->csrf 정책 오류가 나올수도...

http "httpbin.org/get" x==1 y==2
http --form post "httpbin.org/post" x=1 y="hello"
http --json post "httpbin.org/post" x=1 y="hello"
http delete "httpbin.org/delete"

* 참고 사이트 : httpie.org/run

## 😎CBV😎

1. 왜 views.py를 사용합니까?
function(상속X), class(상속O)는 callable object로 정의합니다.
djnago의 view는 callable object로 정의합니다.

2.  CBV의 목적?
중복 제거, 간단한 만큼 미리 약속된 것들이 많음!

## 😎Rest Architecture😎

REST : representational state transfer 자원을 대표하는 단어 or 식별자로 자원의 상태를 전송하는 방법
REST 설계 조건 : REST가 되기 위한 필요충분조건
1. server - client
2. stateless
3. cache
4. uniform interface
4.1 Identification of resources
4.2 Manipulation of resources through representations
4.3 self-descriptive messages : 메세지는 그 하나만으로 모든 것이 설명되어야 합니다.
4.4 hypermedia as the engine of application state(HATEOAS) : 에플리케이션의 상태는 하이퍼링크를 이영해서 전이되어야 합니다.
5. layered system
6. code-on-demand

API : Application Program interface
API : (특정 형식에 맞게)서버와 클라이언트 사이의 메신저
Rest API : REST 아키텍쳐 스타일을 따르는 API

Restful API in django
(Model)Form vs (Model)Serializer
Form/ModelForm vs Serializer/ModelSerializer
HTML Form vs JSON 문자열
is_valid() 함수 사용 vs ... 

## 😎Rest Architecture😎

설치 : pip install djangorestframework
