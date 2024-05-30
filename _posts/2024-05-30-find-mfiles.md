---
layout: post
title: find files with multiple extensions in Linux
date: 2024-05-30 08:39 +0900
description: 리눅스에서 다양한 확장자에 대한 파일명과 상대경로를 찾는 방법
category: [linux, tip]
tags: [find]
pin: false
math: true
mermaid: true
---

## 논리적 OR (-o) 사용

여러 확장자를 찾기 위해 `-o` 플래그를 사용할 수 있습니다. 예를 들어 `.jpg`와 `.png` 파일을 모두 찾으려면 다음 명령을 실행하십시오:

> 예시 : find [검색시작폴더위치] [옵션:검색대상 타입] [검색할 파일 확장자]

```sh
$ find ./ -type f -iname \*.jpg -o -iname \*.png 
```
{: .nolineno }

| 옵션       |   설명                                  |
|-----------|---------------------                    |
| `-type f` | 파일(디렉토리가 아닌)을 검색                    |
| `-iname`  |  대소문자를 구분하지 않고 일치 (ex: jpg, JPG) |
| `-name`   | 대소문자를 구분하여 일치                      |
| `-o`      | 논리적 OR 연산자                           |

이 작업을 수행하려면 괄호와 내용 사이에 공백이 있어야 합니다.

![eg_find](/assets/img/240530/20240530_find.png)

## 정규식 사용

`Linux`에서는 `-regex`를 사용하여 확장자를 간결하게 조합할 수 있습니다. 기본 정규식 구문은 *Emacs* (기본 정규식과 `\\|`와 같은 몇 가지 확장 포함)입니다. 다음과 같이 `.jpg`와 `.png` 파일을 찾을 수 있습니다:

```sh
$ find -regex '.*\\.(jpg|png)'
```
{: .nolineno }

### 여러 확장자 조합

`.sh`, `.txt`, `.c` 확장자를 가진 파일을 찾으려면 다음과 같이 사용할 수 있습니다:

```sh
$ find ./ -type f -name \*.sh -o -name \*.txt -o -name \*.c 
```
{: .nolineno }

> 더 많은 확장자를 추가하려면 간단히 -o 절을 더 추가하면 됩니다. 특정 요구 사항에 따라 경로와 확장자를 조정하시면 됩니다. 😊
{: .prompt-info }
