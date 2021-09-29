# 1. 자바와 웹
## 1.1. 자바(Java)
- 객체지향 프로그래밍
- 뛰어난 재사용성
- 플랫폼 독립적
- 방대한 API
- 우수한 보안
- 멀티스레드 프로그래밍 가능
- '가상 머신(Virtual Machine)'이란 실행 방식을 이용해 WORA(Write Once, Run Anywhere)라는 모토를 가지고 한 번의 작성으로 어떤 플랫폼에서든지 실행할 수 있는 방식으로 동작하는 언어
- 1900년 말 GE(General Electric)사가 썬마이크로시스템즈에 의뢰하여 제임스 고슬링(James Gosling)을 비롯한 개발자들이 어떤 가전제품에서나 동작하는 Oak라는 언어를 개발
- 이후 Oak는 그린 프로젝트로 이름을 바꾸었고 제임스 고슬링은 Oak를 웹에 적용할 수 있는 코드 작업과 C/C++ 언어를 기반으로 하는 머신 구현
- 그린 프로젝트는 1995년에 자바 커피에서 이름을 따서 1.0 버전을 최초로 발표
### 1.1.1. Java SE(Java Platform, Standard Edition)
- 데스크톱, 서버, 임베디드 시스템 개발을 위한 표준 자바 플랫폼으로 자바의 기본 개발 환경 제공
- JDK와 JRE
  - JDK(Java Development Kit): 자바 개발 환경. JVM(Java Virtual Machine)과 컴파일러, 디버거 및 애플리케이션 개발을 위한 도구들이 포함됨.
  - JRE(Java Runtime Environment): JDK의 일부로서 자바 애플리케이션이 실행되는데 필요한 최소한의 요건을 제공. JVM과 핵심적인 클래스들, 각종 지원 파일들로 구성됨.
### 1.1.2. Java EE(Java Enterprise Edition)
- 자바의 기본적인 기능을 정의한 Java SE에 웹서버 역할을 추가한 것
- 자바 애플리케이션을 동작하게 하는 컨테이너 등을 표준화한 스펙
- 기술: JSP, Servlet, EJB, JDBC, JNDI, JTA 등
- WAS(Web Application Server): Java EE 스펙에 따라 제품으로 구현한 것. 대표적으로 Apache Tomcat.
### 1.1.3 Java ME(Java Micro Edition)
- 모바일 장치나 내장형 장치와 같은 소형장치에서 실행되는 자바 애플리케이션을 지원하기 위해 경량화된 기술들을 지원하는 플랫폼
- Java EE와 쉽게 통합 가능
- 소형 단말기의 제한적인 디스플레이 영역을 최대한 활용할 수 있는 UI와 풍부한 이벤트 핸들링 라이브러리 제공(+ KVM, CardVM)
