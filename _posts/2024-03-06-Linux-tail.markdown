---
# multilingual page pair id, this must pair with translations of this page. (This name must be unique)
lng_pair: id_about_tail
title: 리눅스 tail에 대하여

# post specific
# if not specified, .name will be used from _data/owner/[language].yml
author: oh-aram
# multiple category is not supported
category: Linux
# multiple tag entries are possible
tags: [Linux, Command]
# thumbnail image for post
img: ":face.png"
# disable comments on this page
#comments_disable: true

# publish date
date: 2024-03-06 10:00:00 +0900

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
Linux tail 명령어 활용 포스팅
<!-- outline-end -->


### 리눅스 tail 명령어 (실시간 로그 확인)

> tail 명령어  
> tail 명령어는 파일의 마지막 행을 기준으로 지정한 행까지의 파일 내용 일부를 출력해주는 명령어이다. 
> 기본값으로는 마지막 10줄을 출력하며 주로 tail은 리눅스에서 오류나 파일 로그를 실시간으로 확인할 때 매우 유용하게 사용된다.

리눅스에서 tail 명령어는 일반적으로 로그와 같이 시간에 따라 변하는 파일들을 grep과 같은 명령어로 조합해서 실시간으로 업데이트되는 로그를 분석하는데 많이 사용된다.

```python
# 파일 마지막 부분을 출력하는 명령어
$tail [옵션][파일명]
$tail filename.txt
$tail -f filename.txt
```

tail명령어를 사용하시면 해당하는 파일의 마지막 부분을 확인할 수 있다. 위와 같이 쓰면 filename.txt 이라는 파일의 마지막 10줄을 확인하실 수 있다.

### 자주 사용하는 옵션  

***

- ***-f, --follow*** : tail을 종료하지 않고 파일의 업데이트 내용을 실시간으로 계속 출력한다.
- ***-n, --lines (라인 수)*** : 파일의 마지막줄부터 지정한 라인수까지의 내용을 출력한다.
- ***-c, --bytes (바이트 수)*** : 파일의 마지막부터 지정한 바이트만큼의 내용을 출력한다.
- ***-q, --quiet, --silent*** : 파일의 헤더와 상단의 파일 이름을 출력하지 않고 내용만 출력한다.
- ***-v, --verbose*** : 출력하기전에 파일의 헤더와 이름 먼저 출력한 후 파일의 내용을 출력한다.
- ***-s, --sleep, --interval*** : 업데이트의 주기를 설정한다. (-f의 기존 주기 값은 1초이나 이 옵션으로 업데이트 주기를 설정 가능)
- ***-F*** : -f --retry 옵션을 조합한 축약 옵션으로 로그 파일이나 추후에 생성될 파일을 감시하고자할 때 유용하다. 로그파일이 존재하지 않더라도 대기 상태로 프로그램이 종료되지 않다가 해당 파일이 생성되면 로그를 찍는다.
- ***--pid*** : 특정 프로세스가 종료되면 tail을 종료한다.

***

### 실시간 로그 보기 (tail + grep)

```python
$tail -f mylog.log | grep 192.168.15.86
```

파이프를 사용하여 다른 명령어를 조합하여 사용 가능하다. 대부분의 개발자들은 tail과 grep의 명령어를 조합하여 로그파일에서 자신이 원하는 키워드만 추출하곤 한다.
위의 명령어대로 사용하면 mylog파일을 실시간으로 액세스하고 IP주소가 192.168.42.12인 행만 추출할 수 있다.

### 여러 파일을 동시에 표시하는 법
```python
$tail mylog1.log mylog2.log
```
tail명령어의 파일이 여러개를 입력하면 각 파일의 마지막 부분을 확인할 수 있다.

***

***출처 [tail](https://coding-factory.tistory.com/801), [tail2](https://www.lainyzine.com/ko/article/linux-tail-command-print-last-part-of-a-file/)***

