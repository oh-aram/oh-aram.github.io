---
# multilingual page pair id, this must pair with translations of this page. (This name must be unique)
lng_pair: id_about_redis
title: Redis에 대하여

# post specific
# if not specified, .name will be used from _data/owner/[language].yml
author: oh-aram
# multiple category is not supported
category: Server
# multiple tag entries are possible
tags: [server, redis, cache]
# thumbnail image for post
img: ":redis.png"
img_fit: contain
# disable comments on this page
#comments_disable: true

# publish date
date: 2026-03-17 17:30:00 +0900

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
Redis의 개념과 사용 이유 정리
<!-- outline-end -->

### Redis란?

Redis는 **Key-Value 구조의 비정형 데이터를 저장/관리하는 오픈소스 기반 비관계형 DBMS**다.  
인메모리 데이터 구조를 사용하는 저장소라서, 데이터베이스/캐시/메시지 브로커 용도로 널리 사용된다.

>특히 Key-Value 저장소 분야에서 가장 많이 언급되는 기술 중 하나라, 실무에서도 캐시 서버로 자주 선택된다.  

### 데이터베이스가 있는데 Redis를 왜 사용할까?

일반적인 데이터베이스는 데이터를 물리 디스크에 저장하므로 안정성이 높다.  
다만 요청이 많아질수록 디스크 I/O 부담이 커지고, 그만큼 응답 속도가 느려질 수 있다.

서비스 초반에는 `WEB - WAS - DB` 구조만으로도 충분하다.  
하지만 사용자 수가 늘어나고 조회 트래픽이 커지면 DB 과부하가 발생할 수 있고, 이때 Redis 같은 캐시 서버를 도입해 병목을 줄인다.

### 캐시(Cache)란?

캐시는 **한 번 조회한 데이터를 임시 공간에 저장**해 두었다가, 같은 요청이 들어오면 더 빠르게 결과를 반환하는 방식이다.

즉, 매번 DB까지 가지 않고 캐시에서 바로 값을 꺼내기 때문에:

- DB 부하를 줄일 수 있고
- 응답 속도를 빠르게 유지할 수 있으며
- 트래픽 증가 상황에서 성능을 안정적으로 가져가기 좋다

### 캐시 동작 패턴

캐시 서버를 운영할 때 자주 쓰는 패턴은 `Look Aside`와 `Write Back`이다.

#### 1) Look Aside Cache

1. 클라이언트가 데이터를 요청한다.
2. 웹서버는 캐시 서버에 데이터 존재 여부를 먼저 확인한다.
3. 캐시에 데이터가 있으면(Cache Hit), DB 조회 없이 캐시 값을 바로 반환한다.
4. 캐시에 데이터가 없으면(Cache Miss), DB에서 조회한 뒤 캐시에 저장하고 반환한다.

이 방식은 구현이 비교적 단순하고, 조회 성능 개선 효과가 커서 가장 보편적으로 사용된다.

#### 2) Write Back

1. 웹서버는 데이터를 바로 DB에 쓰지 않고 캐시 서버에 먼저 저장한다.
2. 캐시 서버에 일정 시간 데이터가 모인다.
3. 모인 데이터를 배치로 DB에 반영한다.
4. 반영이 끝난 데이터는 캐시에서 정리한다.

핵심 아이디어는 `작은 쓰기 여러 번`보다 `묶어서 한 번에 쓰기`가 효율적일 수 있다는 점이다.

 **주의! 이 방식은 DB에 반영되기 전까지 데이터가 메모리에 머무르기 때문에, 장애가 발생하면 일부 데이터가 유실될 수 있다.**

### Redis 주요 활용 예시

- 조회가 많은 데이터 캐싱(게시글, 상품, 메인 화면 데이터)
- 로그인 세션 저장소
- 대기열(Queue) 처리
- 실시간 랭킹/카운트(예: Sorted Set)

### 본격적인 Redis의 특징

##### 1) Key-Value 구조
복잡한 조인 쿼리보다 `key`로 바로 조회하는 방식이 중심이다.  
그래서 단순 조회/갱신 작업을 빠르게 처리하기 좋다.

##### 2) 인메모리 기반 고속 처리
데이터를 디스크가 아닌 메모리에서 처리하기 때문에, 일반적으로 응답 속도가 매우 빠르다.

##### 3) 다양한 자료구조 지원
Redis는 단순 문자열뿐 아니라 여러 자료구조를 제공한다.

- `String`: 가장 기본적인 Key-Value 형태
- `List`: 배열과 비슷한 순서형 구조(양 끝 삽입/삭제에 강점)
- `Set`: 중복 없는 문자열 집합(태그, 중복 제거 등에 유용)
- `Sorted Set`: 점수(score) 기반 정렬이 가능한 집합(랭킹 보드에 적합)
- `Hash`: 객체 형태 데이터를 필드 단위로 저장할 때 유용

#### 4) Single Threaded 동작
Redis는 기본적으로 단일 스레드로 명령을 처리한다.  
즉, 한 번에 하나의 명령을 처리하므로 오래 걸리는 명령이 들어오면 뒤 요청이 대기할 수 있다.

그럼에도 `GET`, `SET` 같은 단순 명령은 매우 빠르게 처리한다.

### Redis 사용 시 주의할 점

- **장애 대응 플랜 필요**
  - 인메모리 저장소 특성상 장애 상황에서 데이터 유실 가능성이 있으므로, 운영 플랜이 반드시 필요하다.

- **메모리 관리 중요**
  - 메모리를 초과하면 성능 저하나 예기치 않은 삭제 정책(eviction) 문제가 생길 수 있어 TTL/용량 설계가 중요하다.

- **긴 명령은 주의**
  - 싱글 스레드 특성상 처리 시간이 긴 명령은 전체 응답 지연으로 이어질 수 있다.

### 더 알아두면 좋은 Redis 운영 개념

- Replication(Master-Replica)
- Cluster(분산 처리)
- Sentinel(장애 감지/자동 Failover)
- Sharding(데이터 분할)
- Topology 설계

### 한 줄 요약

>Redis는 **"DB 앞단에 두고 조회/쓰기 병목을 줄여 서비스 속도를 높이는 인메모리 Key-Value 저장소"**다.

***출처 [여기 저번에 왔던 것 같은데?](https://wildeveloperetrain.tistory.com/21)***

