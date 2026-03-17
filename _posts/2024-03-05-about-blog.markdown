---
# multilingual page pair id, this must pair with translations of this page. (This name must be unique)
lng_pair: id_about_blog_stack
title: 이 블로그 프로젝트는 어떤 언어로 구성되어 있을까?

# post specific
# if not specified, .name will be used from _data/owner/[language].yml
author: oh-aram
# multiple category is not supported
category: Blog
# multiple tag entries are possible
tags: [jekyll, github-pages, markdown]
# thumbnail image for post
img: ":face.png"
# disable comments on this page
#comments_disable: true

# publish date
date: 2024-03-05 10:00:00 +0900

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
내 블로그 프로젝트의 기술 구성 정리
<!-- outline-end -->

### 이 프로젝트는 어떤 언어를 쓸까?

이 블로그는 **Jekyll 기반 정적 사이트**다.  
그래서 한 가지 언어만 쓰는 구조가 아니라, 역할별로 여러 파일 포맷이 같이 사용된다.

### Jekyll이란?

Jekyll은 **정적 사이트 생성기(Static Site Generator)**다.  
Markdown 글, 템플릿, 설정 파일을 읽어서 최종 HTML/CSS/JS 파일로 빌드해준다.

- DB나 서버 로직 없이도 블로그 운영 가능
- GitHub Pages와 잘 맞아서 배포가 간단함
- 글 작성(콘텐츠)과 화면 구조(템플릿)를 분리하기 좋음

### 구성 요소별 정리

- **Markdown (`.md`, `.markdown`)**
  - 문서 마크업 언어
  - 글 본문 작성용
  - `_posts/` 아래 포스트 파일이 여기에 해당

- **Liquid + HTML (`.liquid`, `.html`)**
  - Liquid: 템플릿 언어
  - HTML: 웹 문서 마크업 언어
  - 페이지 레이아웃, include 컴포넌트, 네비게이션 렌더링
  - 예: `_layouts/`, `_includes/`

- **YAML (`.yml`)**
  - 데이터 직렬화/설정 포맷
  - 사이트 설정/문구/메뉴/데이터 관리
  - 예: `_config.yml`, `_data/conf/main.yml`, `_data/lang/en.yml`

- **SCSS/CSS + JavaScript**
  - SCSS/CSS: 스타일시트 언어
  - JavaScript: 브라우저 스크립트 언어
  - 스타일, UI 동작, 인터랙션 처리
  - 예: `assets/_scss/`, `assets/js/`

- **Ruby (Jekyll 런타임)**
  - 프로그래밍 언어
  - 로컬 빌드/배포 빌드 시 Jekyll이 사이트를 생성
  - 최종 결과물은 정적 HTML/CSS/JS

### 한 줄 요약

이 프로젝트는 "**Markdown으로 글을 쓰고, Liquid 템플릿과 Jekyll(Ruby)로 정적 사이트를 생성하는 구조**"라고 보면 된다.
