# `HTTP` 개관

- 전 세계의 웹 브라우저, 서버, 웹 애플리케이션은 모두 `HTTP`(`Hypertext Trasnfer Protocol`)을 통해 서로 대화.

> `HTTP`는 현대 인터넷의 공용어.

## `HTTP`: 인터넷의 멀티미디어 배달부

- 전 세계의 웹 서버로부터 이 대량의 정보를 빠르고, 간편하고, 정확하게 전송.
- 신뢰성 있는 데이터 전송 프로토콜을 사용하여 전송 중 손상되거나 꼬이지 않음을 보장.
- 개발자는 인터넷의 결함이나 약점에 대한 걱정이 줄어듬.
  > 왜 줄어드는지?

---

## 웹 클라이언트와 서버

- `HTTP` 클라이언트와 `HTTP` 서버는 월드 와이드 웹의 기본 요소.
- 웹 브라우저(클라이언트)는 서버에게 `HTTP` 객체를 요청하고 사용자의 화면에 보여줌.
- 서버는 요청 받은 객체를 찾고, 성공했다면 그것의 타입, 길이 등의 정보와 함께 `HTTP` 응답에 실어서 클라이언트에게 보냄.

---

## 리소스

- 웹 서버는 웹 콘텐츠의 원천인 웹 리소스를 관리하고 제공.
- 웹 서버 파일 시스템의 정적 파일은 가장 단순한 웹 리소스.
- 리소스는 요청에 따라 콘텐츠를 생산하는 프로그램이 될 수도 있음.

### 미디어 타입

- `HTTP`는 웹에서 전송되는 모든 `HTTP` 객체 데이터 각각에 신중하게 `MIME` 타입이라는 데이터 포맷 라벨을 붙임.
- `MIME`(`Multipurpose Internet Mail Extensions`, 다목적 인터넷 메일 확장)은 원래 각기 다른 전자메일 시스템 사이에서 메세지가 오갈 때 겪는 문제점을 해결하기 위해 설계.
  - 이메일에서 워낙 잘 동작했기 때문에 `HTTP`에서도 채택.
    > 그렇다면 다른 방법이 있을까?
- 웹 브라우저는 `MIME` 타입을 통해 다룰 수 있는 객체인지 확인하고 적절한 행동을 실행함.
  > `MIME`에 대한 등록은 브라우저에서 처리하는지? 그렇다면 파서는 브라우저에 내장? 브라우저 사가 모두 개발?
- `MIME` 타입은 슬래시(`/`)로 구분된 주 타입(`primary object type`)과 부 타입(`specific subtype`)으로 이루어진 문자열 라벨.

### `URI`

- 웹 서버 리소스의 이름은 `URI`(`Uniform Resource Identifier`, 통합 자원 식별자)로 지목 가능.
- `URI`는 인터넷의 우편물 주소 같은 것으로, 정보 리소스를 고유하게 식별하고 위치를 지정.

### `URL`

- `URL`(`Uniform Resource Locator`, 통합 자원 지시자)는 리소스 식별자의 가장 흔한 형태.
- 특정 서버의 한 리소스에 대한 구체적인 위치를 서술.
- `URL`은 세 부분으로 이루어진 표준 포맷을 따름.
  1. 스킴(`scheme`): 리소스에 접근하기 위해 사용되는 프로토콜을 서술.
  2. 서버의 주소: 인터넷 주소를 제공.
  3. 웹 서버의 리소스 위치.

> 오늘날 대부분의 `URI`는 `URL`

### `URN`

- `URN`(`Uniform Resource Name`, 통합 자원 이름)은 컨텐츠를 이루는 한 리소스에 대해, 그 리소스의 위치에 영향 받지 않는 유일무이한 이름 역할.
- 이 위치 독립적인 `URN`은 리소스를 여기저기로 옮기더라도 문제없이 동작.
- `URN`은 여전히 실험 중인 상태고 아직 널리 채택되지 않음, 그러나 `URN`의 인프라만 지원된다면 전망은 밝음.

> https://hanamon.kr/%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%81%AC-%EA%B8%B0%EB%B3%B8-url-uri-urn-%EC%B0%A8%EC%9D%B4%EC%A0%90/

---

## 트랜잭션

- `HTTP` 트랜잭션은 요청 명령과 응답 결과로 구성.

### 메서드

- `HTTP` 메서드라 불리는 여러 가지 종류의 요청 명령을 지원.
- 모든 `HTTP` 요청 메세지는 한 개의 메서드를 가짐.
- 메서드는 서버에게 어떤 동작이 취해져야 하는지 전달.

| `HTTP` 메서드 |                                설명                                 |
| :-----------: | :-----------------------------------------------------------------: |
|     `GET`     |            서버에서 클라이언트로 지정한 리소스를 보내라             |
|    `POST`     |     클라이언트 데이터를 서버 게이트웨이 애플리케이션으로 보내라     |
|     `PUT`     | 클라이언트에서 서버로 보낸 데이터를 지정한 이름의 리소스로 저장하라 |
|   `DELETE`    |                  지정한 리소스를 서버에서 삭제하라                  |
|    `HEAD`     |      지정한 리소스에 대한 응답에서, `HTTP` 헤더 부분만 보내라       |

### 상태 코드

- 모든 `HTTP` 응답 메세지는 상태 코드와 함께 반환.
- 상태 코드는 클라이언트에게 요청이 성공했는지 아니면 추가 조치가 필요한지 알려주는 세 자리 숫자.
- `HTTP`는 각 숫자 상태 코드에 텍스트로 된 사유 구절(`reason phrase`)도 함께 보냄.
  - 이 구문은 단지 설명만을 위해서 포함된 것일 뿐 실제 응답 처리에는 숫자로 된 코드가 사용.

### 웹페이지는 여러 객체로 이루어질 수 있다

- 애플리케이션은 보통 하나의 작업을 수행하기 위해 여러 `HTTP` 트랜잭션을 수행.
- 예를 들어, 페이지 레이아웃을 서술하는 `HTML`을 한 번의 트랜잭션으로 가져온 뒤, 이미지 등의 파일을 위해 추가로 트랜잭션 수행.

---

## 메세지

- `HTTP` 메세지는 단순한 줄 단위의 문자열.
  - 이진 형식이 아닌 일반 텍스트.
- 요청 메세지: 웹 클라이언트에서 웹 서버로 보낸 `HTTP` 메세지.
- 응답 메세지: 서버에서 클라이언트로 가는 메세지.
- `HTTP` 메세지는 세 부분으로 구성.
  1. 시작줄: 요청이라면 무엇을 해야하는지, 응답이라면 무슨 일이 일어났는지 기술.
  2. 헤더: 0개 이상의 헤더 필드, 각 헤더 필드는 쉬운 구문 분석을 위해 쌍점(`:`)으로 구분되어 있는 하나의 이름과 하나의 값으로 구성되며, 빈 줄로 끝남.
  3. 본문: 어떤 종류의 데이터든 들어갈 수 있는 메세지 본문이 필요에 따라 올 수 있음.
     - 요청의 본문은 웹 서버로 데이터를 전송.
     - 응답의 본문은 클라이언트로 데이터를 반환.
     - 임의의 이진 데이터, 텍스트를 포함 가능.

---

## `TCP` 커넥션

### `TCP/IP`

- `HTTP`는 애플리케이션 계층 프로토콜로, 네트워크 통신의 핵심적인 세부사항에 대해서 신경 쓰지 않음.
- `TCP/IP`는 대중적이고 신뢰성 있는 인터넷 전송 프로토콜.
- `TCP`(`Transmission Control Protocol`, 전송 제어 프로토콜)
  - 오류 없는 데이터 전송.
  - 순서에 맞는 전달(언제나 보낸 순서대로 도착).
  - 조각나지 않는 데이터 스트림(언제나 어떤 크기로 전송).
- 인터넷 자체가 `TCP/IP`에 기초하고 있으며, `TCP/IP`가 층을 이루는, 패킷 교환 네트워크 프로토콜의 집합.
- `TCP/IP`는 각 네트워크와 하드웨어의 특성을 숨기고, 어떤 종류의 컴퓨터나 네트워크든 서로 신뢰성 있는 의사소통을 제공.
- 일단 `TCP` 커넥션이 맺어지면, 클라이언트와 서버 컴퓨터 간에 교환되는 메세지가 없어지거나, 손상되거나, 순서가 뒤바뀌어 수신되는 일은 결코 없음.
- `HTTP` 프로토콜은 `TCP`의 상위 개념이며, `TCP`는 `IP`의 상위 개념.

### 접속, `IP` 주소 그리고 포트 번호

- 먼저, `IP`(`Internet Protocol`, 인터넷 프로토콜) 주소와 포트 번호를 사용해 클라이언트와 서버 사이의 `TCP/IP` 커넥션을 맺여야 함.
- `TCP` 커넥션을 맺는 것은 전화를 거는 것과 비슷하며, 서버 컴퓨터에 대한 `IP` 주소와 그 서버에서 실행 중인 프로그램(서버)이 사용 중인 포트 번호가 필요.
- `URL`을 통해 리소스에 대한 주소 확인.
  - `IP` 주소 직접 사용.
  - 도메인 이름 혹은 호스트 명은 `DNS`(`Domain Name Service`, 도메인 네임 서비스)라 불리는 장치를 통해 `IP`로 변환.
  - 포트 번호가 없는 경우 기본 값은 `80`.
- `HTML` 리소스를 전달하는 과정.
  1. 웹 브라우저는 서버의 `URL`에서 호스트 명을 추출.
  2. 웹 브라우저는 서버의 호스트 명을 `IP`로 변환.
  3. 웹 브라우저는 `URL`에서 포트 번호(있다면) 추출.
  4. 웹 브라우저는 웹 서버와 `TCP` 커넥션을 맺음.
  5. 웹 브라우저는 서버에 `HTTP` 요청을 보냄.
  6. 서버는 웹 브라우저에 `HTTP` 응답을 돌려줌.
  7. 커넥션이 닫히면 웹 브라우저는 문서를 보여줌.

### `Telnet`(텔넷)을 이용한 실제 예제

- `HTTP`는 이진 형식이 아닌 문자열 기반이기 때문에 웹 서버와 직접 대화하는 것도 간단.
- 텔넷 유틸리티는 입력을 목적지의 `TCP` 포트로 연결해주고, `TCP` 포트에서의 출력을 클라이언트의 출력 장치로 연결해주며, 원격 터미널 세션을 위해 흔히 사용됨.

```shell
telnet www.joes-hardware.com 80

GET /tools.html HTTP/1.1
Host: www.joes-hardware.com
```

---

## 프로토콜 버전

- `HTTP/0.9`
  - `GET` 메서드만을 지원하고 `MIME` 타입, `HTTP` 헤더, 버전 번호는 지원하지 않음.
  - 간단한 `HTML` 객체를 받아 오기 위해 만들어짐.
  - 과거 기술로 심각한 디자인 결함이 있어 금방 대체.
- `HTTP/1.0`
  - 처음으로 널리 쓰이기 시작한 버전.
  - 버전 번호, `HTTP` 헤더, 추가 메서드, `MIME` 타입 처리.
  - 월드 와이드 웹을 대세로 만들었지만 잘 정의된 명세가 아님.
  - 급성작하던 시기에 만들어진, 잘 동작하는 용례들의 모음.
- `HTTP/1.0+`
  - 오래 지속되는 `keep-alive` 커넥션, 가상 호스팅 지원, 프락시 연결 지원들 포함해 많은 기능이 비공식적으로 추가.
- `HTTP/1.1`
  - `HTTP` 설계의 구조적 결함 교정, 두드러진 성능 최적화, 잘못된 기능 제거에 집중.
  - 더 복잡해진 웹 애플리케이션과 배포를 지원.
  - 현재의 `HTTP` 버전.
- `HTTP/2.0`
  - `HTTP/1.1`의 성능 문제를 개선하기 위해 `SPDY` 프로토콜을 기반으로 설계가 진행 중인 프로토콜.

> 진짜 여러가지를 사용하는지? 사용한다면 어디서 쓰고 있는지?

> https://ko.wikipedia.org/wiki/HTTP/2

> https://ko.wikipedia.org/wiki/HTTP/3

---

## 웹의 구성요소

### 프락시

#### 클라이언트와 서버 사이에 위치한 `HTTP` 중개자.

- 웹 보안, 애플리케이션 통합, 성능 최적화를 위한 중요한 구성요소.
- 클라이언트와 서버 사이에 위치하여 클라이언트의 모든 `HTTP` 요청을 받아 서버에 전달.(대개 요청 수정 작업)
- 주로 보안을 위해 사용되며, 모든 웹 트래픽 흐름 속에서 신뢰할 만한 중개자 역할을 함.
- 요청과 응답을 필터링 함.

> 클라이언트와 서버 사이의 트래픽을 전달.

### 캐시

#### 많이 찾는 웹페이지를 클라이언트 가까이에 보관하는 `HTTP` 창고.

- 웹 캐시와 캐시 프락시는 자신을 거쳐 가는 문서들 중 자주 찾는 것의 사본을 저장해 두는, 특별한 종류의 `HTTP` 프락시 서버.
- 훨씬 더 빨리 문서를 다운 받게 하며, `HTTP`는 캐시를 효율적으로 동작하게 하고 캐시된 콘텐츠를 최신 버전으로 유지하면서 동시에 프라이버시도 보호하기 위한 많은 기능을 제공.

> 캐시 프락시는 성능 향상을 위해 자주 찾는 문서의 사본을 저장.

### 게이트웨이

#### 다른 애플리케이션과 연결된 특별한 웹 서버.

- 다른 서버들의 중개자로 동작하는 특별한 서버.
- 주로 `HTTP` 트래픽을 다른 프로토콜로 변환하기 위해 사용.
- 언제나 스스로가 리소스를 갖고 있는 진짜 서버인 것처럼 요청을 다룸.
- 클라이언트는 자신이 게이트웨이와 통신하고 있음을 알아채지 못 함.
- `HTTP/FTP` 게이트웨이는 `FTP URI`에 대한 `HTTP` 요청을 받아들인 뒤, `FTP` 프로토콜을 이용해 문서를 가져옴.

### 터널

#### 단순히 `HTTP` 통신을 전달하기만 하는 특별한 프락시.

- 두 커넥션 사이에서 날(`raw`) 데이터를 열어보지 않고 그대로 전달해주는 `HTTP` 애플리케이션.
- 주로 비 `HTTP` 데이터를 하나 이상의 `HTTP` 연결을 통해 그대로 전송해주기 위해 사용.
- 암호화된 `SSL` 트래픽을 `HTTP` 커넥션으로 전송함으로써 웹 트래픽만 허용하는 사내 방화벽을 통과시키는 것이 있음.

### 에이전트

#### 자동화된 `HTTP` 요청을 만드는 준지능적(`semi-interligent`) 웹 클라이언트.

- 사용자 에이전트라고도 하며, 사용자를 위해 `HTTP` 요청을 만들어주는 클라이언트 프로그램.
- 웹 요청을 만드는 애플리케이션은 뭐든 `HTTP` 에이전트.
- 웹 브라우저 또한 에이전트이며, 자동화된 사용자 에이전트인 스파이더나 웹 로봇 등도 있음.
