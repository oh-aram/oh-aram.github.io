---
# multilingual page pair id, this must pair with translations of this page. (This name must be unique)
lng_pair: id_about_docker
title: Docker에 대하여

# post specific
# if not specified, .name will be used from _data/owner/[language].yml
author: oh-aram
# multiple category is not supported
category: Server
# multiple tag entries are possible
tags: [docker, devops]
# thumbnail image for post
img: ":docker.png"
img_fit: contain
# disable comments on this page
#comments_disable: true

# publish date
date: 2026-03-19 10:00:00 +0900

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
Docker의 개념과 흐름 정리
<!-- outline-end -->

### Docker란?

도커는 애플리케이션을 신속하게 구축, 테스트 및 배포할 수 있는 소프트웨어 플랫폼이다.  
소프트웨어를 컨테이너라는 표준화된 유닛으로 패키징하며, 컨테이너는 라이브러리, 시스템 도구, 코드 등 소프트웨어 실행에 필요한 모든 것이 포함되어 있다.

즉, 도커는 컨테이너 환경에서 독립적으로 애플리케이션을 실행할 수 있도록 컨테이너를 만들고 관리하는 것을 도와주는 도구이다.  
도커를 통해 애플리케이션을 실행하면 독립적인 환경에서 일관된 결과를 보장한다.

도커의 핵심 개념은 이미지와 컨테이너다.

Docker는 애플리케이션을 **컨테이너(Container)** 단위로 패키징하고 실행할 수 있게 해주는 플랫폼이다.


- 개발 환경과 운영 환경의 차이를 줄일 수 있고
- 설치/배포 과정을 표준화하기 쉽고
- 팀 단위 협업에서 동일한 실행 환경을 공유하기 좋다

### 컨테이너
컨테이너는 격리된 공간에서 프로세스가 동작하는 기술이다.  
기존의 가상화 방식이 OS가상화가 아닌 프로세스를 격리하는 방식으로 동작한다.  
리눅스에서 프로세스를 격리하는 방식을 리눅스 컨테이너라고 한다.

단순히 프로세스를 격리하기 때문에 가볍고 빠르다.  
또한 CPU나 메모리는 프로세스가 필요한 만큼만 추가 사용하여서 성능적으로 거의 손실이 없다.

아래 그림은 도커(왼쪽)와 가상머신(오른쪽)을 나타낸 것이다.

![Docker container vs VM](/assets/img/posts/docker-container.png)

##### 컨테이너의 특징

- 서버에 여러 컨테이너를 실행하면 독립적으로 실행되어 VM을 사용하는 느낌을 준다.
- 실행 중인 컨테이너에 접속하여 명령어를 입력할 수 있다.
- CPU나 메모리 사용량을 제한할 수 있다.
- apt-get이나 yum등 운영체제에서 사용하는 패키지 매니저를 통해 설치할 수 있고 사용자도 추가하고 프로세스를 백그라운드로 실행할 수 있다.
- 호스트의 특정 포트와 연결하거나 호스트의 특정 디렉토리를 내부 디렉토리인 것처럼 사용 가능
- 새로운 컨테이너를 만드는데 1~2초로 매우 빠르다.

> **여기서! apt-get이 뭐임?**
>
> 조사한 바로는 apt 및 apt-get은 Ubuntu와 같은 Debian 기반 Linux 배포판에서 사용되는 패키지 관리(설치/삭제/업데이트) 도구다.  
> apt와 apt-get 두 가지가 있는 모양.  
> apt가 인간친화적인 통합 명령어이고 apt-get은 기존부터 있던 안정적 저수준 도구라고 함.  
> 약간 like vi 와 vim 같은 느낌스.
>
> **예시**
> ```bash
> apt install nginx
> apt remove nginx
> apt purge nginx   # 설정까지 삭제
> ```

### 이미지

컨테이너 실행에 필요한 파일과 설정을 포함하고 있는 것으로 상태값을 가지지않고 변하지 않는다. 컨테이너는 이미지를 실행한 상태이다. 추가되거나 변하는 값은 컨테이너에 저장된다.
도커이미지는 Docker hub에 등록하거나 Docker Registry 저장소를 직접 만들어 관리할 수 있다.

##### 이미지 특징
- 도커이미지 용량은 보통 MB~GB이지만 가상머신에 비하면 적응 용량
- 상태값을 가지지 않고 변하지 않는다.
- 하나의 이미지를 통해 여러 컨테이너를 생성할 수 있고 컨테이너를 삭제해도 이미지는 변하지 않음
- 이미지들은 Docker Hub를 통해 버전 관리 및 배포가 가능
- 도커는 **Dockfile**이라는 파일로 이미지를 만든다.

### Dockerfile이란?

도커 이미지를 만들기 위해 Dockerfile이라는 파일에 DSL(Domain Specific Language) 언어를 이용해 이미지를 생성할 수 있다. 단순 텍스트 파일로 일반적으로 소스와 함께 관리한다. 서버에서 프로그램을 설치하려고 할 때 Dockerfile 을 통하여 관리하면 된다. Dockerfile에서 사용할 수 있는 키워드는 20개 정도 있다. 여기서 중요한 건 `FROM` 과 `RUN` 이다. 

`FROM` 과 `RUN` 으로 이미지를 만들 수 있다.
##### FROM

```dockerfile
FROM <image>:<tag>
FROM ubuntu:16.04
```

베이스 이미지를 지정한다. 반드시 베이스 이미지를 지정해야 하며 어떠한 이미지도 베이스 이미지가 될 수 있다. tag는 버전을 지정하는 것으로 가능하면 구체적인 버전을 지정하는 것이 좋다.

##### RUN

```dockerfile
RUN <command>
RUN bundle install
```

가장 많이 사용하는 구문 중 하나로 말 그대로 명령어를 실행한다. 내부적으로 /bin/sh -c 뒤에 명령어를 실행하는 방식

### 왜 Docker를 사용할까?

- 로컬/운영 환경 불일치 문제를 줄이기 위해
- 서비스 배포를 더 빠르고 일관되게 만들기 위해
- 여러 서비스를 분리해 독립적으로 관리하기 위해

### Docker 핵심 개념

- **Image**: 실행에 필요한 파일/설정/라이브러리를 담은 템플릿

- **Container**: Image를 기반으로 실제 실행 중인 인스턴스

- **Dockerfile**: Image를 만들기 위한 빌드 스크립트 파일

- **Registry**: Image를 저장하고 공유하는 공간 (예: Docker Hub)

### 기본 실행 흐름

1. `Dockerfile` 작성
2. `docker build`로 Image 생성
3. `docker run`으로 Container 실행
4. 필요 시 `docker push`로 Registry 배포

#### 사용 시 주의할 점

- 이미지 크기가 너무 커지지 않도록 관리하기
- 민감 정보는 이미지에 직접 넣지 않기
- 볼륨/네트워크 설정을 명확히 관리하기

### 한 줄 요약

Docker는 **"애플리케이션 실행 환경을 컨테이너로 표준화해서 개발/배포를 쉽게 만드는 도구"**다.


***출처 [AWS](https://aws.amazon.com/ko/compare/the-difference-between-apt-and-apt-get/), [Tecoble](https://tecoble.techcourse.co.kr/post/2021-08-14-docker/)***


