---
description: 정리하는 중입니다.
---

# Kang

## 의문점

1.  **HTTP 완벽 가이드 10P, 1.4.3 웹 페이지는 여러 객체로 이루어질 수도 있다.**
    이 부분에 대한 자세한 설명이 있었으면 좋겠다, 정확히 어떠한 의미로 서술되어 있는 것인지, 감이 잘 오지 않는다.
2.  **HTTP 완벽 가이드 19~20P, 1.8 웹의 구성 요소**
3.  

---



## 1장 HTTP 개관

이 챕터는 아래의 내용에 대해서 이야기할 것이다.

1. 얼마나 많은 클라이언트와 서버가 통신을 하는지
2. 리소스 \(웹 콘텐츠\)가 어디서 오는지
3. 웹 트랙잭션이 어떻게 동작하는지
4. HTTP 통신을 위해 사용되는 메시지의 형식
5. HTTP 기저의 TCP 네트워크 전송
6. 여러 종류의 HTTP 프로토콜
7. 인터넷 곳곳에 설치된 다양한 HTTP 구성 요소

### 1.1 인터넷 멀티미디어 배달부

인터넷 상에는 텍스트, 이미지, 영상 등 다양한 형식의 정보가 존재한다. HTTP는 이 정보들을, 사람들의 PC에 설치된 브라우저로, 이 대량의 정보를 정확하고 신속하게 전달한다. HTTP는 **신뢰성 있는 데이터 전송 프로토콜**을 사용하기 때문에, 데이터가 전송 중에 꼬이거나 손상되지 않음을 보장할 수 있다. 덕분에 사용자, 그리고 개발자들은 자신의 정보의 무결성에 대해서, 직접 확인할 필요가 사라졌다. 개발자들은 이제 인터넷의 결함이나 약점에 대한 걱정없이 애플리케이션 고유의 기능을 구현하는 데에 집중할 수 있다.

### 1.2 웹 클라이언트와 서버

웹 콘텐츠는 웹 서버에 존재한다. 웹 서버는 HTTP 프로토콜로 소통하기 때문에 HTTP 서버라고도 한다. 이들 웹 서버는 인터넷에 데이터를 저장하고, HTTP 클라이언트가 요청한 데이터를 제공한다. 예를 들어, 특정 도메인의 html을 열어볼 경우, 웹 브라우저는 해당 도메인의 웹 서버로 HTTP 요청을 보낸다. 서버는 요청을 해석하여 html을 찾고, 성공할 시 그것의 타입과 길이 등 부가적인 정보와 함께 클라이언트에게 돌려준다. 이 때도 역시 HTTP 응답에 실어서 보낸다.

### 1.3 리소스

웹 서버는 웹 리소스를 관리하고 제공한다. 가장 단순한 웹 리소스는 웹 서버 파일 시스템의 정적 파일이다. 그러나 모든 리소스가 정적일 필요는 없다. 리소스는 요청에 따라 콘텐츠를 생산하는 프로그램이 될 수도 있다. 라이브 영상을 보여주거나, 주식 거래, 부동산 데이터 베이스 검색, 온라인 쇼핑몰이 그러하다.

#### **1.3.1 미디어 타입**

각기 다른 전자 메일 시스템 사이에서 메시지가 오갈 때 겪는 문제점을 해결하고자, **MIME\(Multi purpose Internet Mail Extensions**, 다목적 인터넷 메일 확장\)이 만들어졌다. 이것이 매우 잘 동작했기 때문에 HTTP에서도 멀티미디어 콘텐츠를 기술하고 라벨을 붙이기 위해서 채택되었다. 웹 서버는 모든 HTTP 객체 데이터에 MIME 타입을 붙인다. 웹 브라우저는 서버로부터 객체를 돌려 받을 때 다룰 수 있는 객체가 맞는지, MIME 타입을 통해서 확인할 수 있다. MIME 타입은 사선\(/\)으로 구분된 주 타입\(Primary object type\)과 부 타입\(specific subtype\)으로 이루어진 문자열 라벨이다. 예를 들면 아래와 같다.

* html로 작성된 텍스트 문서 &gt; text/html
* plain ASCII 텍스트 문서 &gt; text/plain
* JPEG 이미지 &gt; image/jpeg
* GIF 이미지 &gt; image/gif
* 애플 퀵 타임 동영상 &gt; video/quicktime
* 마이크로소프트 파워포인트 프레젠테이션 &gt; application/vnd.ms-powerpoint

#### **1.3.2 URI**

웹 서버 리소스는 각자 이름을 가지고 있어서 클라이언트는 이를 통해 리소스를 지목할 수 있다. 이 리소스 이름을 통합 자원 식별자\(URL, Uniform Resource Identifier\) 라고 한다. 클라이언트는 이 URI을 가지고 정보 리소스, 즉 웹에 있는 이미지나 영상 등 단일 객체를 하나 하나 지목할 수 있다.

> [http://www.joes-hardware.com/specials/saw-blade.gif](http://www.joes-hardware.com/specials/saw-blade.gif)
>
> 첫째, HTTP를 사용하라.
>
> 둘째, [www.joes-hardware.com](www.joes-hardware.com)으로 이동하라
>
> 셋째, /specials/saw-blade.gif 라는 이름의 리소스를 가져와라.

#### **1.3.2.1 URL**

통합 자원 지시자\(URL, Uniform Resource Locator\)는 리소스 식별자의 가장 흔한 형태이다. 오늘 날 대부분 URI는 URL의 형태로 되어 있다. 대부분의 URL은 세 부분으로 이루어진 표준 포맷을 따르는데, 첫번째 부분은 스킴, 두번째 부분은 서버의 인터넷 주소, 세번째는 리소스를 가리킨다. 여기서 스킴이란, 리소스에 접근하기 위한 프로토콜로, 보통은 HTTP 프로토콜\(http://\) 이다.

#### **1.3.2.2 URN**

URI의 두번쨰 종류는 유니폼 리소스 이름 \(URN, Uniform Resource Name\)이다. URN은 콘텐츠를 이루는 한 리소스에 대해, 그 리소스의 **위치에 영향을 받지 않는 유일무이한 이름 역할**을 한다. 이 위치 독립적인 URN은 어디에 있든 문제없이 동작한다. 리소스가 이름을 유지하는 한, 다른 프로토콜로 접근하더라도 문제가 없다. URN은 효율적인 동작을 위해 리소스 위치를 분석하는 인프라 자원이 필요한데, 이는 아직 부재 중이다. 따라서 아직 실험 중인 상태고 널리 채택되지 않았다. URN의 전망은 밝지만, 이러한 까닭에 편의 및 통상적인 관례에 따라 URI와 URL의 별도 구분을 두지 않는다.



### 1.4 트랙잭션

HTTP 트랙잭션은 요청 명령과 응답 결과로 이루어져 있다.

* 요청 명령
  * GET / special/saw-blade.gif HTTP/1.0 Host: [www.joes-hardware.com](www.joes-hardware.com)
* 응답 결과
  * HTTP/1.0 200 OK Content-type: image/gif Content-length: 8572

#### **1.4.1 메서드**

HTTP 요청 메시지는 1개의 메서드를 가진다. 메서드는 서버에서 어떤 동작이 취해져야 하는지를 뜻한다. 흔히 GET, PUT, DELETE, POST, HEAD를 쓴다.

#### 1.4.2 상태 코드

모든 HTTP 응답 메시지는 상태 코드를 가진다. 상태 코드는 클라이언트에게 요청에 대한 결과를 알려주는 세 자리 숫자이다.

#### 1.4.3 웹 페이지는 여러 객체로 이루어질 수도 있다

웹 브라우저는 ‘시각적으로 풍부한’ 웹 페이지를 호출할 때 여러 차례의  HTTP 트랜잭션을 수행한다. HTML을 가져온 후, 나머지 리소스들을 위한 트랜잭션이 실행된다. 이 때, 리소스들은 각기 다른 서버에 존재할 수도 있다. **웹 페이지는 리소스가 아닌, 리소스의 모음이다.**



### 1.5 메시지

위에, 트랜잭션은 요청과 응답으로 이루어져 있고, 다시 그것들은 메서드, 상태 코드 등으로 이루어져 있다고 서술하였다. 각 메시지들을 더 자세히 볼 때, HTTP 메시지들은 아래와 같은 특징을 지닌다.

1.  **이진 형식이 아닌 일반 텍스트(String)**이기 때문에 사람이 읽고 쓰기 편하게 되어 있다. 
    어떤 프로그래머들은, 이진 형식이나 엄격한 텍스트 구조였다면 처리가 편하고 속도가 빨랐을 것이라고 말하지만, HTTP는 확장과 디버그가 용이하여 대다수에게는 좋은 평가를 받고 있다.
2.  요청과 응답 결과는 유사한 형식으로 이루어져 있는데, 아래의 세 가지 구조를 지닌다.
    1.  시작 줄 : 요청이라면 무엇을 해야 하는 것인지, 응답이라면 무엇이 일어났는지를 말한다.
        (GET /test/hi-there.txt HTTP/1.0 또는 HTTP/1.0 200 OK)
    2.  헤더 (header) : 시작 줄 다음에는 0개 이상의 헤더 필드가 존재하고, 이 헤더 필드는 쌍점으로 구분되어 하나의 이름에 하나의 값을 지닌다.
        헤더는 한 줄에 1개 씩만 존재하며, 마지막에는 빈 줄 하나를 두어 본문과 구분을 둔다.
    3.  본문 (body) : 요청의 본문은 웹 서버로 데이터를 보내며, 응답은 역으로 반환한다. 본문은 임의의 이진 데이터를 포함할 수도 있다. (ex. image)

#### 1.5.1 간단한 메시지의 예

책 본문 참고 바람.



### 1.6 TCP 커넥션

TCP (Transmission Control Protocol, 전송 제어 프로토콜) 커넥션을 통해 메시지는 한 곳에서 다른 곳으로 이동된다.

#### 1.6.1 TCP/IP

HTTP는 애플리케이션 계층 프로토콜이다. HTTP는 네트워크 통신의 핵심적인 세부 사항에 대해서 신경쓰지 않는다. 이러한 과정은 신뢰성 있고 대중적인 프로토콜인 TCP/IP 에게 맡긴다. TCP는 아래의 세 가지를 제공한다.

1.  오류 없는 데이터 전송
2.  순서에 맞는 전달 (데이터는 보낸 순서로 도착한다.)
3.  조각나지 않는 데이터 스트림 (언제든 어떤 크기로든 보낼 수 있다.)
    -   속도 면에서 우수하나 위의 특성을 지니지 못한 것으로, UDP 프로토콜이 있으니, 관심있는 사람은 별도로 확인하길 바람.

인터넷 자체가 TCP/IP에 기초하고 있는데, **TCP/IP란 TCP와 IP가 층을 이루는, 패킷 교환 네트워크 프로토콜의 집합**이다. TCP/IP는 각 네트워크와 하드웨어의 특성을 숨기고, 어떤 종류의 컴퓨터나 네트워크든 서로 신뢰성 있는 의사소통을 하게 해준다. 일단 TCP 커넥션이 맺어지면 클라이언트와 서버 컴퓨터 간에 교환되는 메시지가 없어지거나, 손상되거나, 순서가 바뀌는 일은 켤고 없다.
네트워크 개념 상 HTTP 프로토콜은 TCP 위의 계층이다. 계층 순서는 4계층, 5계층, 7계층 등 경우에 따라 따로 분리하곤 하는데, 이 책의 HTTP 네트워크 프로토콜 스택은 HTTP > TCP > IP > 네트워크를 위한 인터페이스 > 물리적인 네트워크 하드웨어로 이어진다.

#### 1.6.2 접속. IP 주소 그리고 포트번호

HTTP 클라이언트는 서버에 메시지를 전송하기 전에 TCP/IP 커넥션을 맺어야 한다. TCP/IP는 두 컴퓨터 사이의 연결선 역할을 수행한다. TCP에서는 서버 컴퓨터에 대한 IP 주소와, 실행 중인 프로그램의 포트 번호를 필요로 한다. **이 IP주소와 포트 번호가 다시 앞에서 말한 URL**이다. **도메인**(또는 호스트 명)으로 되어 있는 경우도, DNS(Domain Name Service)에 의해 쉽게 IP주소와 포트 번호로 변환이 가능하다.

1.  웹 브라우저는 서버의 URL에서 호스트 명을 추출한다.
    1.  만약 URL이 도메인으로 되어 있다면, 서버의 호스트 명을 IP로 변환한다. 대부분은 이 단계를 거쳐야 한다.
    2.  URL에 포트 번호가 있다면, 포트 번호를 추출한다.
2.  웹 브라우저는 웹 서버와 TCP 커넥션을 맺는다.
3.  웹 브라우저는 서버에 HTTP 요청을 보낸다.
4.  서버는 웹 브라우저에 HTTP 응답을 보낸다.
5.  커넥션이 닫히고, 웹 브라우저는 문서를 보여준다.

#### 1.6.3 텔넷을 이용한 실제 예제

책 본문 참고 바람.



### 1.7 프로토콜 버전

-   HTTP/0.9 : 오직 GET 메서드만 지원,  HTML 객체를 받기 위한 용도였으며 금방 1.0 VER로 대체되었다.
-   HTTP/1.0 : 웹페이지와 상호작용하기 위한 다양한 기능이 추가되었으나, 잘 정의되지 않은, 용례들의 모음에 가깝다.
-   HTTP/1.0+ : 비공식적으로나마 keep-alive 커넥션, 가상 호스팅, 프락시 연결 지원 등이 사실 상 표준으로 추가되었다.
-   **HTTP/1.1** : HTTP의 설계 구조적 결함 교정, 성능 최적화, 잘못된 기능 제거에 초점을 맞추었다, 현재 사용되고 있는 Version이다.
-   **HTTP/2.0** : 구글의 SPDY 프로토콜 기반으로 설계가 진행 중인 프로토콜이다.



### 1.8 웹의 구성 요소

-   **프락시** : 클라이언트와 서버 사이에 위치 **HTTP 중개 서버**
-   **캐시** : 많이 찾는 웹 페이지를 클라이언트 가까이에 보관하는 HTTP 창고
-   **게이트웨이** : 다른 애플리케이션과 연결된 특별한 웹 서버
-   **터널** : HTTP 통신을 전달하기만 하는 특별한 프락시
-   **에이전트** : 자동화된 HTTP 요청을 만드는 준 지능적(semi-intelligent) 웹 클라이언트



#### 1.8.1 프락시

웹 보안, 애플리케이션 통합, 성능 최적화를 위한 HTTP 구성 요소.
프락시는 클라이언트와 서버 사이에 위치하여, 클라이언트의 HTTP 요청을 중개하여, 클라이언트를 대신해 요청을 서버에 전달한다. 이 중개 과정에서 요청은 대개 수정이 된다.  이는 주로 보안을 위해 사용되며, 반대로 응답을 필터링하기도 한다. 예를 들어, 응답 내에 바이러스를 검출하거나 유해 콘텐츠를 차단하는 데에도 쓰인다.

#### 1.8.2 캐시

웹 캐시와 캐시 프락시는 **자주 찾는 것의 사본**을 저장해두는 특별한 **HTTP 프락시 서버**이다. 프락시는 클라이언트와 서버 사이에 중개한다고 했는데, 만일 요청의 결과가 이미 프락시가 가지고 있는 종류의 것이라면, 서버에 요청을 보내지 않고 프락시에서 처리한다. 이로 인해서 클라이언트는 더 빨리 문서를 다운로드할 수 있게 된다. HTTP는 캐시를 효율적으로 동작하게 하고 캐시된 컨텐츠를 최신으로 유지하면서, 동시에 프라이버시를 보호하기 위한 기능을 정의한다.

#### 1.8.3 게이트웨이

게이트웨이는 다른 서버들의 중개자 역할을 하는 특별한 서버이다. 주로 HTTP 트래픽을 다른 프로토콜로 변환하기 위해 사용하며, 언제나 자기 자신이 리소스를 가지고 있는 진짜 서버인 것처럼 동작한다. 따라서 클라이언트는, 자신과 통신하고 있는 개체가 게이트웨이임을 알 수 없다.

#### 1.8.4 터널

두 커넥션 사이에서 날(Raw) 데이터를 열어보지 않고 그대로 전달하는 HTTP 애플리케이션. 터널은 주로 비 HTTP 데이터를 하나 이상의 HTTP 연결을 통해 전송해주기 위해 사용된다. 비 HTTP 데이터, 예컨대 암호화된 SSL 트래픽을 전송하여 웹 트래픽만 허용하는 사내 방화벽 내부로 보낼 수 있다.

#### 1.8.5 에이전트

에이전트는 HTTP 요청을 만드는 클라이언트 프로그램이다. 웹 브라우저도 에이전트에 해당한다. 다른 종류로는 사람의 통제 없이 웹을 돌아다니며 HTTP 트랜잭션을 일으키고, 콘텐츠를 받아오는, ‘스파이더’, ‘웹로봇’ 같은 크롤링 엔진들도 있다. 검색 엔진도 이에 해당한다.