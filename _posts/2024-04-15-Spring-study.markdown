---
# multilingual page pair id, this must pair with translations of this page. (This name must be unique)
lng_pair: id_about_spring
title: JAVA SPRING의 탄생

# post specific
# if not specified, .name will be used from _data/owner/[language].yml
author: oh-aram
# multiple category is not supported
category: Spring
# multiple tag entries are possible
tags: [spring, study]
# thumbnail image for post
img: ":face.png"
# disable comments on this page
#comments_disable: true

# publish date
date: 2024-04-15 10:00:00 +0900

# seo
# if not specified, date will be used.
#meta_modify_date: 2022-02-10 08:11:06 +0900
# check the meta_common_description in _data/owner/[language].yml
#meta_description: ""

# optional
# please use the "image_viewer_on" below to enable image viewer for individual pages or posts (_posts/ or [language]/_posts folders).
# image viewer can be enabled or disabled for all posts using the "image_viewer_posts: true" setting in _data/conf/main.yml.
#image_viewer_on: true
# please use the "image_lazy_loader_on" below to enable image lazy loader for individual pages or posts (_posts/ or [language]/_posts folders).
# image lazy loader can be enabled or disabled for all posts using the "image_lazy_loader_posts: true" setting in _data/conf/main.yml.
#image_lazy_loader_on: true
# exclude from on site search
#on_site_search_exclude: true
# exclude from search engines
#search_engine_exclude: true
# to disable this page, simply set published: false or delete this file
#published: false
---

<!-- outline-start -->
node 버전 관리 포스팅
<!-- outline-end -->

### JAVA SPRING의 탄생

자바 스프링을 공부하면서 정리하는 포스팅 입니다. chapter 1

### chapter 1
***

**EJB** 
스프링이 나오기 전에 EJB를 사용 했었다. 하지만 EJB는 좋은 기능들이 많았지만 너무나도 복잡하고 개발하기에 어려움이 많았다.
<kbd>EJB</kbd> -> <kbd>하이버네이트</kbd> -> <kbd>JPA</kbd>

#### 스프링의 역사
        
* 2002년 로드 존슨이 EJB의 문제점을 지적하는 책을 출간
* EJB가 없어도 충분히 고품질의 확장 가능한 애플리케이션을 개발할 수 있음을 보여주고 지금의 스프링 핵심 개념과 기반 코드가 들어가 있음
* 책 출간 이후 유겐휠러와 얀 카로프가 로드 존슨에게 오픈소스 프로젝트를 제안하였고 스프링의 핵심 코드의 상당수는 유겐 휠러가 지금도 개발
* 스프링의 이름은 전통적인 J2EE(EJB)라는 겨울을 넘어 새로운 시작이라는 뜻으로 지음
        
#### 스프링 부트
* 스프링을 편리하게 사용할 수 있도록 지원, 최근에는 기본으로 사용
* 단독으로 실행할 수 있는 스프링 애플리케이션을 쉽게 생성
* Tomcat 같은 웹 서버를 내장해서 별도의 웹 서버를 설치하지 않아도 됨
* 손쉬운 빌드 구성을 위한 starter 종속성 제공
* 스프링과 3rd parth(외부) 라이브러리 자동 구성
* 메트릭, 상태 확인, 외부 구성같은 프로덕션 준비 기능 제공
* 관례에 의한 간결한 설정
* 스프링과 스프링부트는 별도로 사용할 수 있는 것이 아님 기본적으로 스프링 부트를 사용해서 도와주는 역할
        
### 스프링
***스프링이라는 단어는 문맥에 따라 다르게 사용됨 (애매함)***
        
 - 스프링 DI 컨테이너 기술
 - 스프링 프레임워크
 - 스프링 부트, 스프링 프레임워크 등을 모두 포함한 스프링 생태계
        
### 핵심 개념  
***이 기술을 왜 만들었는가? 이 기술의 핵심 컨셉은?***
        
#### 스프링의 진짜 핵심
- 스프링은 자바 언어 기반의 프레임워크
- 자바 언어의 가장 큰 특징 - **객체 지향 언어**
- 스프링의 객체 지향 언어가 가진 강력한 특징을 살려내는 프레임워크
- 스프링은 **좋은 객체 지향** 애플리케이션을 개발할 수 있게 도와주는 프레임워크
- EJB 시절에는 상속에 얽메여 EJB에 의존하여 개발하다 보니 객체 지향의 장점을 잃어버려 순수한 자바로 돌아가자는 뜻의 POJO라는 말도 생겼었다.
        
### 객체 지향 특징
 - 추상화
 - 캡슐화
 - 상속
 - 다형성 (Polymorphism)
        
### 객체 지향 프로그래밍
- 객체 지향 프로그래밍은 컴퓨터 프로그램을 명령어의 목록으로 보는 시각에서 벗어나 여러개의 독립된 단위, 즉 "객체"들의 모임으로 파악하고자 함이다.
- 각각의 객체는 메시지를 주고받고, 데이터를 처리할 수 있다.(협력)
- 객체 지향 프로그래밍은 프로그램을 유연하고 변경이 용이하게 만들어 대규모 소프트웨어 개발에 많이 사용된다.
        
### 역할과 구현을 분리
- 역할과 구현으로 구분하면 세상이 단순해지고, 유연해지며 변경도 편리
- 장점
  - 클라이언트는 대상의 역할(인터페이스)만 알면 된다.
  - 클라이언트는 구현 대상의 내부 구조를 몰라도 된다.
  - 클라이언트는 구현 대상의 내부 구조가 변경되어도 영향을 받지 않는다.
  - 클라이언트는 구현 대상 자체를 변경해도 영향을 받지 않는다.
  - 객체 설계시 역할(인터페이스)을 먼저 부여하고, 그 역할을 수행하는 구현 객체 만들기
        
#### 다형성의 본질
- 인터페이스를 구현한 객체 인스턴스를 실행 시점에 유연하게 변경할 수 있다.
- 다형성의 본질을 이해하려면 협락이라는 객체사이의 관게에서 시작해야함
- 클라이언트를 변경하지 않고, 서버의 구현 기능을 유연하게 변경할 수 있다.
        
### 정리
- 실세계의 역할과 구현이라는 편리한 컨셉을 다형성을 통해 객체 세상으로 가져올 수 있음
- 유연하고, 변경이 용이
- 확장 가능한 설계
- 클라이언트에 영향을 주지 않는 변경 가능
- 인터페이스를 안정적으로 잘 설계하는 것이 중요
        
### 한계
- 역할(인터페이스) 자체가 변하면, 클라이언트, 서버 모눋에 큰 변경이 발생한다.
- 인터페이스를 안정적으로 잘 설계하는 것이 중요
        
### 스프링과 객체 지향
- 다형성이 가장 중요
- 스프링은 다형성을 극대화해서 이용할 수 있게 도와준다
- 스프링에서 이야기하는 제어의 역전(IoC), 의존관계 주입(DI)은 다형성을 활용해서 역할과 구현을 편리하게 다룰 수 있도록 지원한다.
- 스프링을 사용하면 마치 레고 블럭 조립하듯이 구현을 편리하게 변경할 수 있다.
        
# SOLID 원칙
클린코드로 유명한 로버트 마틴이 좋은 객체 지향 설계의 5가지 원칙을 정리
- **SRP(Single responsibility principle): 단일 책임 원칙**
  - 한 클래스는 **하나의 책임**만 가져야 한다.
  - 하나의 책임이라는 것은 모호 가장 중요한 기준은 변경이다. 변경의 파급효과가 적으면 단일 책임 원칙을 잘 따른 것
        
  - **OCP(Open/Close principle): 개방-폐쇄 원칙**
    - 소프트웨어 요소는 **확장에는 열려 있으나 변경에는 닫혀 있어야 한다.**
    - 다형성을 활용
    - 인터페이스를 구현한 새로운 클래스를 하나 만들어서 새로운 기능을 구현
    - MemberService 클라이언트가 구현 클래스를 직접 선택
      - MemberRepository m = new MemoryMemberRepository(); //기존 코드
      - MemberRepository m = new JdbcMemberRepository();
    - 구현 객체를 변경하려면 클라이언트 코드를 변경해야 한다.
    - 분명 다형성을 사용했지만 OCP원칙을 지킬 수 없다.
    - 객체를 생성하고, 연관관계를 맺어주는 별도의 조립, 설정자가 필요하다.
        
   - **LSP(Liskov subsitution principle): 리스코프 치환 원칙**
     - 프로그램의 객체는 프로그램의 정확성을 깨뜨리지 않으면서 하위 타입의 인스턴스로 바쑬 수 있어야 한다.
     - 다형성에서 하위 클래스는 인터페이스 규약을 다 지켜야 한다는 것, 다형성을 지원하기 위한 원칙, 인터페이스를 구현한 구현
     - 단순한 컴파일의 성공하는 것을 넘어서는 이야기
     - ex) 자동차 인터페이스의 엑셀을 앞으로 가라는 가능, 뒤로 가게 구현하면 LSP 위반, 느리더라도 앞으로 가야함
   
   - **ISP(interface segregation principle): 인퍼테이스 분리 원칙**
     - 특정 클라이언트를 위한 인터페이스 여러 개가 범용 인터페이스 하나보다 낫다
     - 자동차 인터페이스 -> 운전 인터페이스, 정비 인터페이스로 분리
     - 사용자 인터페이스 -> 운전자 클라이언트, 정비사 클라이언트로 분리
     - 분리하면 정비 인터페이스 자체가 변해도 운전자 클라이언트에 영향을 주지 않음
     - 인터페이스가 명화해지고, 대체 가능성이 높아진다.
   
   - **DIP(Dependency inversion principle): 의존관게 역전 원칙**
     - 프로그래머는 **"추상화에 의존해야지 구체화에 의존하면 안된다."** 의존성 주입은 이 원칙을 따르는 방법 중 하나다.
     - 쉽게 이해해서 구현 클래스에 의존하지 말고, 인터페이스에 의존하라는 뜻
     - 앞에서 이야기한 역할(Role)에 의존하게 해야 한다는 것과 같다. 객체 세상도 클라이언트가 인터페이스에 의존해야 유연하게 구현체를 변경할 수 있다!
       구현체에 의존하게 되면 변경이 아주 어려워진다.
     - 그런데 OCP에서 설명한 MemberService는 인터페이스에 의존하지만, 구현 클래스도 동시에 의존한다.
     - MemberService 클라이언트가 구현 클래스를 직접 선택
       - MemberRepository m = new MemoryMemberRepository();
     - DIP 위반
   
### 정리
   - **객체 지향의 핵심은 다형성**
   - **다형성 만으로는 쉽게 부품을 갈아 끼우듯이 개발할 수 없다.**
   - **다형성 만으로는 구현 객체를 변경할 떄 클라이언트 코드도 함꼐 변경된다.**
   - **다형성 만으로는 OCP, DIP를 지킬 수 없다.**
        
#### 스프링 이야기에 왜 객체 지향 이야기가 나오는가?
   - **스프링은 다음 기술로 다형성 + OCP, DIP를 가능하게 지원**
     - DI(dependency Injection): 의존관계, 의존겅 주입
     - DI 컨테이너 제공
   - 클라이언트 코드의 변경 없이 기능 확장
   - 쉽게 부품을 교체하듯이 개발
   - 옛날 어떤 개발자가 좋은 객체 지향 개발을 하려고 OCP,DIP 원칙을 지키면서 개발을 해보니 너무 할일이 많고 배꼽이 배보다 커져 프레임워크로 만들어버림
   - ***실무 고민***
     - 인퍼테이스를 도입하면 추상화라는 비용이 발생
     - 기능을 확장할 가능성이 없다면, 구체 클래스를 직접 사용하고, 향후 꼭 필요할 때 리팩터링해서 인터페이스를 도입하는 것도 방법이다.

