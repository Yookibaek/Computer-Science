### 면접 질문 모음
1. TCP와 UDP 차이에 대해 설명하시오
  * [TCP와 UDP](tcp와-udp)
2. HTTP와 TCP 관계에 대해 설명하시오
3. HTTP와 HTTPS에 차이와 HTTPS에서 S는 어떤 계층에 속했는지 설명하시오
  * [HTTP와 HTTPS](http와-https)
4. REST와 SOAP에 대해 설명하시오
  * [REST와 RESTful의 개념](#rest-api)
5. 쿠키와 세션에 대해 설명해주세요
  * [쿠키와 세션](쿠키와-세션)
6. 샤딩이란 무엇인가요?
7. 게임에서는 TCP와 UDP중 어떤 방식을 주로 사용할까요?
8. 3way handshake와 4way handshake를 설명해 주세요.
  * [TCP와 UDP](tcp와-udp)
9. get방식과 post 방식 그리고 CRUD에 대해 설명해주세요.
  * [HTTP 메서드](http-메서드)
10. TCP와 IP에 대해 설명해주세요
  *[OSI 7 계층](osi-7-계층)
11. HTTP Method에 대해 설명해주세요
  * [HTTP 메서드](http-메서드)
12. Connection Timeout/Read Timeout의 차이는?
13. Restful 하지 않다는 것은 무슨 의미인가요?


## OSI 7 계층
![OSI 7계층](https://github.com/WeareSoft/tech-interview/raw/master/contents/images/osi-7-layer.png)
- **Application Layer**
- **Transport Layer**
  - TCP: End to End사용자들이 신뢰성 있는 데이터를 주고 받을 수 있도록 해준다.
  - UDP: 신뢰성은 보장하지 않지만, 그래서 속도가 더 빠름
- **Network Layer**
  - IP: 여러개의 노드를 거칠때마다 경로를 찾아주는 역할을 하는 계층.
- **Physical Layer**

## TCP와 UDP
- 네트워크 계층 중 전송 계층(Transport Layer)에서 사용하는 프로토콜
- TCP
  - **연결형** 서비스
  - 3-way handshaking과정을 통해 연결을 설정하고, 4-way handshaking을 통해 연결을 해제한다.
  - 흐름제어 및 혼잡제어 제공
    - 흐름제어
      - 데이터를 송신하는 곳과 수신하는곳 데이터 처리속도 조절하여 수신자의 버퍼 오버플로우 방지
      - 윈도우 크기를 조절해가며 전송
    - 혼잡제어
      - 네트워크 내 패킷 수 넘치지않게 전송하는 것
  - Full-Duplex, Point to Point 방식
    - 전송이 양방향
    - 각연결이 정확히 2개의 종단점 가짐
    - 멀티캐스팅이나 브로드캐스팅 지원 안함
- UDP
  - **비 연결형** 서비스
  - checksum필드로 최소한의 오류만 검출
  - 신뢰성보다는 연속성이 중요한 서비스, 예를들면 실시간 서비스(streaming)에 사용
- TCP의 3 way handshake와 4 way handshake
  - 3-way hand shake란
    - ![IMAGE](https://github.com/WeareSoft/tech-interview/raw/master/contents/images/3-way-handshaking.png)
    - TCP통신을 이용하여 네트워크 연결하는 과정
  - 4-way hand shake 란
    - ![IMAGE](https://github.com/WeareSoft/tech-interview/raw/master/contents/images/4-way-handshaking.png)
    - TCP연결을 해제하는 과정

## HTTP와 HTTPS
- HTTP 프로토콜
  - 개념
    - HyperText Transfer Protocol
    - 웹 상에서, 클라이언트가 서버에게 Request를 보내고, 서버가 이에 대한 응답을 Response하는 방식으로 정보를 교환하는 프로토콜
    - TCP/IP 기반으로 동작(80번 포트)하는, Application Layer의 프로토콜 이다.
    - 주로 HTML 문서를 주고받는 데에 쓰인다. 물론 JSON, XML, Plane text등도 교환 가능하다.
    - 비연결(Connectionless)
      - 클라이언트가 request를 서버에 보내고 서버가 response를 보내면 연결이 끊김
    - 무상태(stateless)
      - 연결 끊으면 상태 정보를 유지하지 않는다
- HTTPS 프로토콜
  - HyperText Transfer Protocol over Secure Socket Layer
  - HTTPS는 새로운 애플리케이션 계층의 프로토콜이 아니다. HTTP는 원래 TCP와 직접 통신했지만, HTTPS에서 HTTP는 SSL과 통신하고 SSL이 TCP와 통신하게 된다. 
  - 공통키, 공개키..
  
## HTTP 메서드
- HTTP 프로토콜을 이용해서 서버에 데이터(요청 정보)를 전달할 때 사용하는 방식
- POST 메서드(Create, Insert)
  - 개념
    - 서버의 값이나 상태를 바꾸기 위한 용도의 메서드
    - **수행하는것(Insert, Update, Delete)**
  - 사용방법
    - 요청 정보를 HTTP 패킷의 Body 안에 숨겨서 서버로 전송한다.
  - 특징
    - Body 안에 숨겨서 요청 정보를 전송하기 때문에 대용량의 데이터를 전송하기에 적합하다.
    - GET 방식보다 보안상 안전하다.
  - Q. 조회하기 위한 용도로 POST가 아닌 GET 방식을 사용하는 이유는?
    - 1. 설계 원칙에 따라 GET 방식은 서버에게 여러 번 요청을 하더라도 동일한 응답이 돌아와야 함.
    - 2. 웹에서 모든 리소스는 Link할 수 있는 URL을 가지고 있어야 한다.

- GET 메서드(Read, Select)
  - 개념
    - 정보를 조회하기 위한 메서드
    - 서버에서 어떤 데이터를 가져와 보여주기 위한 용도의 메서드
    - **가져오는 것(Select)**
  - 사용 방법
    - URL 끝에 ?가 붙어서 요청정보가(Key=value) 쌍을 이루어 붙는다
    - 여러개의 key-value를 전달하려면 &로 구분한다.
  - 특징
    - HTTP 패킷의 Body는 비어 있는 상태로 전송
    - GET 방식은 캐싱을 사용할 수 있어, GET REQUEST와 서버로 부터의 Response가 브라우저에 의해 캐쉬 된다.
    
- PUT 메서드(Update)
  - URI로 지정한 서버의 파일을 대체한다
  - 보안적으로 위험해 일반적으로 비활성화.
- DELETE 메서드(Delete) 
  - URI로 지정한 서버의 파일을 삭제한다
  - 보안적으로 위험해서 일반적으로 비활성화.

## 쿠키와 세션
- 비 연결 지향(Connectinoless)
  - 
  
- 쿠키와 세션의 필요성
  - 이전요청과 현재 요청이 같은 사용자의 요청인지 알기 위해서는 상태를 유지해야 한다.
  - HTTP 프로토콜에서 상태를 유지하기 위한 기술로 쿠키와 세션이 있다.
- 쿠키(Cookie)란?
  - 개념
    - 클라이언트 로컬에 저장되는 키와 값이 들어있는 파일
  - 구성 요소
    - 쿠키 이름
    - 쿠키 값
    - 쿠키 만료시간
  - 동작 방식
    1. 웹브라우저가 서버에 요청
    2. 상태를 유지하고 싶은 값을 쿠키(cookie)로 생성
    3. 서버가 응답할때 HTTP헤더(Set-Cookie)에 쿠키를 포함해서 전송
    4. 전달받은 쿠키는 웹브라우저에서 관리하고 있다가, 다음 요청때 쿠키를 HTTP헤더에 넣어서 전송
    5. 서버는 쿠키 정보를 읽어 이전 상태 정보를 확인한 후 응답
  - 쿠키 사용 예
    - 아이디, 비밀번호 저장
    - 쇼핑몰 장바구니
    
- 세션(Session) 이란?
  - 개념
    - 일정 시간 동안 같은 브라우저로부터 들어오는 요청을 하나의 상태로 보고 그 상태를 유지하는 기술
    - 웹 브라우저를 통해 서버에 접속한 이후부터, 브라우저를 종료할 때까지 유지되는 상태
    
  - 동작 방식
    1. 웹브라우저가 서버에 요청
    2. 서버가 해당 웹브라우저(클라이언트)에 유일한 ID(Session id) 부여함
    3. 서버가 응답할 때 HTTP 헤더(Set-Cookie)에 Session ID를 포함해서 전송.  
    4. 웹브라우저는 이후 웹브라우저를 닫기까지 다음 요청 때 부여된 Session ID가 담겨있는 쿠키를 HTTP 헤더에 넣어서 전송.
    5. 서버는 세션 ID를 확인하고, 해당 세션에 관련된 정보를 확인한 후 응답
  - 세션 사용 예
    - 로그인
    
- 쿠키와 세션의 차이점
  - 저장위치
    - 쿠키: 클라이언트
    - 세션: 서버
  - 보안
    - 쿠키: 클라이언트에 저장되므로 보안에 취약하다.
    - 세션: 쿠키를 이용해 Session ID만 저장하고 이 값으로 구분해서 서버에서 처리하므로 비교적 보안성이 좋다.
  - 라이프사이클
    - 쿠키: 만료시간에 따라 브라우저를 종료해도 계속해서 남아 있을 수 있다.
    - 세션: 만료시간을 정할 수 있지만 브라우저가 종료되면 만료시간에 상관없이 삭제.
    
## REST API
  - REST란
    - Representational State Transfer - 대표적인 상태 전달
    - REST는 네트워크 상에서 Client와 Server 사이의 통신 방식 중 하나
    - **HTTP URI(Uniform Resource Identifier)를 통해 Resource를 명시하고, HTTP Method(Post, Get, Put, Delete)를 통해 해당 자원에 대한 CRUD Operation을 적용하는 것을 의미한다.**
    - 자원 기반의 구조(Resource Oriented Architecture)라 해서 ROA 라고 도 함.
    - 웹사이트의 이미지, 텍스트, DB내용 등의 모든 자원에 고유한 ID인 HTTP URI를 부여함
  - REST 장단점
    - 장점
      - 여러 가지 서비스 디자인에서 생길 수 있는 문제를 최소화 해준다.
  - REST가 필요한 이유
    - 애플리케이션 분리 및 통합
    - 다양한 클라이언트의 등장
    - 즉, 최근의 서버 프로그램은 다양한 브라우저와 안드로이드폰, 아이폰과 같은 모바일 디바이스에서도 통신을 할 수 있어야 한다.
  - REST 구성요소
    1. 자원(Resource): URI
      - 모든 자원에 고유한 ID가 존재하고, 이 자원은 Server에 존재한다.
      - 자원을 구별하는 ID는 '/groups/:group_id'와 같은 HTTP URI
    2. 행위(Verb): HTTP Method
      - HTTP 프로토콜의 Method를 사용한다.
      - HTTP 프로토콜은 GET, POST, PUT, DELETE, HEAD와 같은 메서드를 제공한다.
        
    3. 표현(Representation of Resource)
      - Client가 자원의 상태에 대한 조작을 요청하면 Server는 이에 적절한 응답(Representation)을 보낸다.
      - JSON 혹은 XML을 통해 데이터를 주고 받는 것이 일반적이다.
      
  - REST API
    - REST API의 정의
      - REST 기반으로 서비스 API를 구현한 것
      - 최근 OpenAPI(구글맵, 공공데이터 등), 마이크로 서비스등을 제공하는 업체 대부분은 REST API를 제공한다.
    - REST API의 특징
      - REST는 HTTP표준을 기반으로 구현하므로, HTTP를 지원하는 프로그래밍언어로 클라이언트,서버 구현할 수 있다.
      - 즉, REST API를 제작하면 자바,C#,등등 이용해 클라이언트 제작할 수 있다.
    - REST API 설계 기본 규칙
       1. URI에 정보의 자원을 표현해야 한다.
        - Resource는 영어 소문자
       2. 자원에 대한 행위는 HTTP Method(GET,PUT,POST,DELETE등)로 표현한다
       
    - REST API 설계 규칙
  - RESTful
    - RESTful의 개념
      - REST원리를 따르는 시스템들을 RESTful 하다고 한다.
    - RESTful의 목적
    - RESTful하지 못한 경우

## 소켓
### Socket.io와 WebSocket의 
