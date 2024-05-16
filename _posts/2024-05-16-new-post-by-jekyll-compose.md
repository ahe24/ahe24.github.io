---
layout: post
title: New post by Jekyll compose
date: 2024-05-16 10:23 +0900
description:
category: [Blogging, jekyll]
tags: [jekyll, compose]
pin: false
math: true
mermaid: true
---

## Jekyll Compose 를 사용하여 빠른 포스팅

포스트는 `_posts` 폴더에 생성되는데 파일명은 `yyyy-mm-dd-title.md` 형식으로 생성해야 하며, 상단의 헤더에 여러 설정을 입력해야 한다. 이러한 반복 작업을 줄이기 위해 `jekyll-compose`를 사용하여 빠르게 포스팅을 생성할 수 있다.

### Jekyll Compose 설치

자신의 Github Page 루트 디렉토리에서 `Gemfile`을 편집기로 열어서 아래의 설정을 추가해 준다.

```text
gem 'jekyll-compose', '~> 0.12.0'
```
{: .nolineno }

CMD 명령창에서 아래와 같이 입력하여 `jekyll-compose` 를 설치한다.

```sh
# gem install jekyll-compose
Successfully installed jekyll-compose-0.12.0
Parsing documentation for jekyll-compose-0.12.0
Done installing documentation for jekyll-compose after 0 seconds
1 gem installed
# 
```
{: .nolineno }

### _config.yml 수정

`_config.yml` 하단의 아래와 같이 `jekyll_compose` 부분을 설정하여, 포스트 레이아웃을 추가한다.

```yaml
jekyll_compose:
  default_front_matter:
    posts:
      description:
      image:
        path:
        alt:
      category: []
      tags: []
      pin: false
      math: true
      mermaid: true
```
{: .nolineno }

### 새로운 포스트 생성

CMD 명령창에서 아래의 포스트 생성 명령어를 입력하면 `config.yml`에서 설정한 레이아웃으로 입력된 헤더와 함꼐 `“yyyy-mm-dd-title.md”` 파일이 자동으로 생성된다.

```sh
# bundle exec jekyll compose "New post test"
Configuration file: D:/Z7_Github/ahe24.github.io/_config.yml
New post created at _posts/2024-05-16-new-post-test.md
# 
```
{: .nolineno }
