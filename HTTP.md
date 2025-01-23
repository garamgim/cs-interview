https://www.youtube.com/watch?v=aRdr0nylmGk&list=LL&index=2&t=2s

### HTTP

- 인터넷을 맨 처음 만들었을때 FTP, TELNET 등의 프로토콜이 존재.
- 90년대 들어서 브라우저가 등장하면서 HTTP 프로토콜이 보급됨을 계기로 인터넷이 대중화되었다.

<br>

### 클라이언트 - 서버

- 인터넷의 모든 서비스는 클라이언트-서버 프로세스간에 데이터 교환으로 이루어진다.
- 클라이언트 프로세스 - 서비스 요청
- 서버 프로세스 - 서비스 제공
- Peer-to-peer (P2P) 모델에서 peer는 경우에 따라 서버 역할 혹은 클라이언트 역할을 하는 프로세스를 의미한다.

<br>

### Web

- Web 페이지는 HTML Text 문서와 object들로 구성된다.
- object는 HTML file, 텍스트 file, 이미지 file 등 다양한 형태로 이루어진다.
- Object file들이 저장된 장소는 URL 주소로 표시한다.
- Object들은 다른 여러 Web page들로 연결되어있다.
- URL 예: HostIP/filepath/object(00.jpg)

<br>

### HTTP (Hypertext Transfer Protocol)

- HTTP는 브라우저(client)와 웹 서버간에 정보를 주고 받는 메시지의 형태와 절차를 규정한 프로토콜이다.
- HTTP는 두가지 메시지가 정의되어있다. (Request와 Response)
- TCP 포트번호 80 (HTTP 서버 주소)을 사용한다.

<br>

### Request와 Response Messages

<image src="resources/01.png">
<image src="resources/02.png">
<image src="resources/03.png">
<image src="resources/04.png">

<br>

### Status Code

- 200 OK
  - 요청 성공, 요청된 object가 이 메시지에 포함
- 301 Moved Permanently
  - 요청한 object는 이동되었음, 이동된 위치는 이 메시지에 포함
- 304 Modified
  - 캐시에 있는 정보 전달
- 400
  - 요청 메시지를 이해할 수 없음
- 404
  - 요청한 문서를 이 서버에서 찾을 수 없음

<br>

### HTTP 연결 절차

- 클라이언트는 서버에 TCP 연결을 요청 (포트번호 80)
- 서버는 TCP 연결 요청 수락
- 클라이언트와 서버 사이에 HTTP 메시지 교환
- TCP 연결 해제

<br>

### stateless

- 서버는 클라이언트의 과거 요청의 상태에 대해 어떤 기록도 하지 않는다.
- 따라서 HTTP에 대한 TCP 연결은 클라이언트와 서버간의 한번의 요청과 응답이 발생하면 TCP 연결은 해제된다.

<br>

### HTTP 연결의 종류

- Nonpersistent HTTP
  - 한개의 개체(object) 전송이 종료되면 TCP 연결도 종료된다.
  - 따라서 다음번 전송을 위해서 다시 TCP 연결을 설정해야한다.
  - HTTP/1.0은 nonpersistent HTTP
- Persistent HTTP
  - 한번의 TCP 연결을 통해 여러개의 개체를 전송할 수 있다.
  - HTTP/1.1은 디폴트 모드로서 persistent connection 사용

<br>

### Cookies: 클라이언트 정보

원래 HTTP 디자인 한사람들은 쿠키를 별로 좋아하지 않았다. stateless한 상태를 해치기 때문.

<image src="resources/05.png">

- 4가지 요소
  - 서버가 보내는 HTTP response message의 cookie 헤더라인 `set-cookie`
  - 클라이언트(브라우저)가 이를 cookie file에 저장
  - HTTP request message에 헤더라인 `cookie`에 이를 함께 전송
- 예) 장바구니에 고른 물건이 그대로 있음
- 장점
  - 약간의 인증, 정보 기억, 추천, 세션 상태
- 단점
  - 개인정보 노출

<br>

### 웹 캐시 (Web Cache)

<image src="resources/06.png">

- 위치
  - 캐시는 client와 server에서 모두 동작
  - 일반적으로 캐시는 인터넷 서비스 사업자(ISP)에 설치됨
  - 하지만 인트라넷(기관에서 운영하는 인터넷)을 운영하는 기관(학교, 기업)에서도 캐시를 운영
- 장점
  - Client request에 대한 응답 시간을 단축
  - 액세스 망의 트래픽 양을 감소시킴
