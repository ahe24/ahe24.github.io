---
layout: post
title:  "Jenkins Out of memory"
date:   2024-05-02 15:37:29 +0900
description: Jenkins 툴 연동시 오류 문제
category: [jenkins, Install]
tags: [jenkins]
pin: false
math: true
mermaid: true
---

## Jenkins 툴 연동시 Out of Memory 오류

```sh
# *** Could not allocate 44278 gigabytes
# Fatal   : Out of memory. [system-0]
#         : Executable aborted.
# 
```
{: .nolineno }

## Global Properties 설정

아래와 같이 설정하거나 workspace 폴더의 내용을 제거한다.

![jenkins_global_env](</assets/img/jenkins_global_env1.png>)
