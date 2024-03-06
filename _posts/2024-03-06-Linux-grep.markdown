---
# multilingual page pair id, this must pair with translations of this page. (This name must be unique)
lng_pair: id_about_grep
title: 리눅스 grep에 대하여

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
date: 2024-03-06 14:00:00 +0900

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

***

### 리눅스 grep

```python
$grep [옵션] [패턴] [파일명]
$grep -i "ERROR" 2023-04-03.log
```
특정 파일에서 지정한 문자열이나 정규표현식을 포함한 행을 출력해주는 명령어로 pipe(|)를 사용해 다른 명령어와 사용하는 경우가 많다.

<br>

### grep의 종류 

| 명령어   | 설명          |  정규표현식 가능 여부 |  
|-------|:------------|-------------:|  
| grep  | 다중 패턴 검색    |            O |  
| egrep | 정규표현식 패턴 검색 |            O |  
| fgrep | 문자열 패턴 검색   |            X |    
  
<br>

### grep 명령어 옵션

- ***-i*** : 대소문자를 구분하지 않는다.
- ***-n*** : 줄의 번호와 내용을 같이 검색
- ***-m*** : 최대 출력 수 제한
- ***-v*** : 문자가 포함되지 않는 행 검색
- ***-w*** : 단어 단위로 문자열 검색 
- ***-H*** : 검색 결과 앞에 파일 이름 표시하여 검색
- ***-r*** : 하위 디렉토리를 포함한 모든 파일에서 문자 검색
<br>

***사용 예시***
```python
1. grep -i "문자열" [파일 명] 
grep -i "error" app_2023_04_03.log

2. grep -n "문자열" [파일 명] 
grep -n "error" app_2023_04_03.log -> "error"문자열이 포함된 라인 번호 출력.

3. grep -m [라인수] "문자열" [파일 명]
grep -m 50 "error" app_2023_04_03.log -> "error"문자열이 포함된 결과 50개까지 출력.

4. grep -v "문자열" [파일 명]
grep -v "error" app_2023_04_02.log -> "error"문자열이 포함되지 않은 라인 출력.

5. grep -w "문자열" [파일 명]
grep -w "error" app_2023_04_02.log -> "error"문자열(단어 단위) 포함된 라인 출력.

6. grep -H "문자열" *
grep -H "error" * -> "error"문자열이 포함된 파일 이름 표시.

7. grep -r "문자열" *
grep -r "error" * -> 하위 디렉토리에 있는 파일까지 포함하여 모든 파일에서 "error"문자열 검색
grep "error" * -> 현재 디렉토리에 있는 모든 파일 중 "error"문자열 검색
```
<br>

### grep 명령어 자주 사용하는 검색 양식
```python
grep "문자열1\|문자열2" [파일명]         -> 여러 문자열을 한번에 검색
grep "문자열1" [파일명] | grep "문자열2" | grep "문자열3"    -> 여러 문자열을 한번에 검색
grep "문자열" [파일명] >> [저장할 파일명] -> *원하는 내용을 출력하여 파일로 재가공*
grep "^문자열" [파일명]                  -> 문자열로 행이 시작되는 경우 검색 
grep "^[he]" [파일명]                   -> h나 e로 시작하는 모든 행 검색
grep "문자열&" [파일명]                  -> 문자열로 행이 끝나는 경우 검색
grep "h*" [파일명]                      -> "h"로 시작하는 모든 로우 검색
grep -A2 "문자열" [파일명]               -> 해당 문자열이 들어강 행을 포함해 아래 2행 검색
grep -v "문자열" [파일명]                -> 해당 문자를 제외한 행 검색
grep "문자열" *                         -> 현재 위치의 모든파일 (*)에서 특정 문자열 검색
grep [a-c] [파일명]                     -> a,b,c로 시작하는 로우를 검색
grep "h...e" [파일명]                   -> h로 시작하고 e로 끝나는 단어 검색
```

***실시간 로그 검색***
```python
$ tail -f [파일명] \| grep "ERROR"
```
위와 같이 명령어를 사용하면 "ERROR"라는 글씨를 포함한 로그가 출력되는 자주 사용하는 명령어 형식이다.  

***

***출처 [Back-end공부하는 Hero의 개발공부일기:티스토리](https://backhero.tistory.com/16), [개발괘발개발새발](https://velog.io/@inhwa1025/Linux-grep-command)***

