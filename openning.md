---
description: 서문 역시 책을 공부하는 데에 도움이 될 거라 생각하고 기재합니다.
---

# 서문

### HTTP 완벽 가이드

**웹은 어떻게 동작하는가?**

#### 하이퍼텍스트 전송 프로토콜 \(HTTP, yperText Transfer Protocol\)

**서문 : 이 책은 무얼 말하고자 하는가?**

> HTTP의 header에 대해서 말하고자 한 거라면 수백 페이지의 책을 쓰지 못했을 것.

* HTTP를 어떻게 사용하는가?
* HTTP를 왜 사용하는가?
* HTTP를 조사하는 데에 독자들이 시간을 줄일 수 있도록 http를 동작하는 데 필요한 주요 기술 소개. 이 부분에 대해서는, http의 연관 기술들도 같이 설명하도록 한다.
* **HTTP나 웹의 기본적인 구조를 이해하고 싶어 하는 독자**를 대상으로 한 책.
* 소프트웨어, 하드웨어 기술자는 HTTP 및 관련 웹 기술에 대한 참고서로 활용 가능.
* 시스템 아키텍나 네트워크 관리자는 복잡한 웹 아키텍처를 어떻게 설계, 배포, 관리할 것인지 배울 수 있다.

#### 목차

1. **HTTP 웹의 기초** : HTTP 핵심 기술과 웹 기초
   1. **HTTP 개관** : HTTP에 대한 개략적인 내용
   2. **URL\(Uniform Resource Locator\)과 리소스** : URL의 포맷과 URL이 가리키는 리소스의 다양한 형식, RUL에서 더 진화된 URN에 대한 내용
   3. HTTP 메세지 : HTTP 메세지가 어떻게 웹 content를 전송하는가
   4. **커넥션 관리** : HTTP 관리에 대한 흔한 오해와 잘못 작성된 규칙 및 동작들에 대한 설명
2. **HTTP 아키텍처** : HTTP 서버, 프락시 ,캐시, 게이트웨, 로봇 애플리케이션 등 웹 시스템을 구성하는 빌딩 블록
   1. **웹 서버** : 웹 서버 아키텍처에 대한 개요
   2. **프락시** : HTTP를 전달하고 제어함으로써 플랫폼 역할을 하는 중개 서버인 HTTP 프락시 서버에 대한 설명
   3. **캐싱** : 자주 사용하는 문서를 로컬에 복제하여 성능을 높이고 부하는 낮추는 웹 캐시 동장 방식에 대한 설명
   4. **통합점** : 게이트웨이, 터널, 릴레이: 보안 소켓 계층 등 HTTP가 아닌 프로토콜 소프트웨어를 HTTP로 잇는 게이트웨이, 애플리케이션 서버
   5. **웹 로봇** : 유비쿼터스 브라우저, 로봇, 스파이더, 검색엔진 등 웹 전반에서 쓰이는 클라이언트
   6. **HTTP/2.0** : 현재 개발이 진행 중인 HTTP/2.0 프로토콜
3. **식별, 인가, 보안** :
   1. **클라이언트 식별과 쿠키** : 특정 사용자만 볼수 있는 콘텐츠를 제공하는 데 쓰이는 사용자 식별 기술
   2. **기본 인증** : 사용자 식별의 기본 체계, 데이터베이스에서의 HTTP 인증
   3. **다이제스트 인증** : HTTP의 보안을 강화하기 위해 제안된 개선사항
   4. **보안 HTTP** : 인터넷 암호화, 디지털 인증서, SSL
4. **엔터티, 인코딩, 국제화**
   1. **엔터티와 인코딩** : HTTP 콘텐츠의 구조
   2. **국제화** : 웹 컨텐츠를 전 세계 유저가 읽을 수 있도록 다른 언어와 문자로 변환해주는 웹 표준
   3. **내용 협상과 트랜스 코딩** : 적절한 컨텐츠를 받기 위한 협상 체계
5. **콘텐츠 발행 및 배포**
   1. **웹 호스팅** : 현대 웹 호스팅 환경에 있는 서버에 배포하는 방법, HTTP 가상 웹 호스팅 지원 방식
   2. **배포 시스템** : 웹 컨텐츠를 생성하고 웹 서버에 그 컨텐츠를 배포하는 기술에 대한 논의
   3. **리다이렉션과 부하 균형** : 유입되는 웹 트래픽을 서버 군에 분배하는 기술과 도구
   4. **로깅과 사용 추적** : 로그 포맷과 그에 대한 일반적인 질문
6. **부록**
   * URi 스킴 : 통합 자원 식별자\(URI, Uniform Resource Identifier\) 스킴을 통해 지원하는 프로토콜.
   * HTTP 상태 코드 : HTTP 응답 코드 목록
   * HTTP 헤더 : HTTP 헤더 필드 목록
   * MIME 타입 : MIME 타입 목록 및 타입 등록 방법
   * base-64 인코딩
   * 다이제스트 인증 : HTTP에서의 다양한 인증 스킴 구현 방법
   * D언어 태그 : HTTP 언어 관련 헤더들에서 사용하는 언어 태그 값
   * MIME 캐릭터 세트 등록 : HTTP 국제화 지원에 사용하는 문자 인코딩에 대한 상세 목록
