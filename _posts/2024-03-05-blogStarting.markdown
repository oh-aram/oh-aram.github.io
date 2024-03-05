---
# multilingual page pair id, this must pair with translations of this page. (This name must be unique)
lng_pair: id_Examples
title: 블로그 로컬 실행

# post specific
# if not specified, .name will be used from _data/owner/[language].yml
author: oh-aram
# multiple category is not supported
category: bundler
# multiple tag entries are possible
tags: [jekyll, ruby, bundler]
# thumbnail image for post
img: ":post_pic1.jpg"
# disable comments on this page
#comments_disable: true

# publish date
date: 2024-03-05 11:57:06 +0900

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

오아람의 개발 블로그를 깃 블로그로 시작하면서 로컬로 블로그를 동작시키는 방법에 대한 내용입니다.
<!-- outline-end -->

# 깃 블로그 로컬 실행 방법
{:data-align="center"}

***

#### Bundler

```python
$bundle exec jekyll serve
```
위의 명령어를 통해 깃 블로그 로컬 실행

해당 명령어로 실행되지 않는 다면 업데이트 후 재실행

그래도 실행되지 않는다면 아래의 Ruby를 업데이트 후 실행

### Ruby

**rbenv를 통해 Ruby 설치**

```python
$rbenv install -l
```

해당 명령어를 통해 설치할 수 있는 Ruby 버전을 확인한다.
{% highlight python %}
$rbenv install -.-.-
{% endhighlight %}


제일 최신 버전의 Ruby를 설치해준 후 **rbenv versions**을 통해 버전을 확인
```python
$which ruby
/usr/bin/ruby
```

아직 ruby는 기존 OS에 설치된 ruby(system)을 가리키고 있다.
```python
$rbenv global -.-.-
```

위의 명령어를 통해 rbenv에 설치된 ruby를 가리키도록 바꿔준다.
```python
$ruby --version
```

명령어를 통해 **rbenv versions** 명령어와 일치하는지 확인

***
### rbenv global 명령을 실행 후에도 ruby 버전이 바뀌지 않는 경우
rbenv global 명령을 실행하고, rbenv versions를 통해 확인한 버전과, ruby --version으로 확인한 버전이 다른 경우가 있다.

이 경우 환경변수 설정이 필요합니다.

rbenv init을 실행하고, 출력되는 eval~ 줄을 2번째 줄에 표시되는 파일 뒤에 붙여넣습니다.
```python
$ rbenv init
#Load rbenv automatically by appending
#the following to ~/.zshrc:

eval "$(rbenv init - zsh)"
```
vim ~/.zshrc 로 뒤에 붙여주거나 echo를 활용
source ~/.zshrc를 통해 수정한 환경변수 적용

***

출처 [Ruby](https://codecamper.me/blog/122/)
