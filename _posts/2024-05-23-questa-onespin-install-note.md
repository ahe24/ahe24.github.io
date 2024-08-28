---
layout: post
title: Questa OneSpin Install Note
date: 2024-05-23 08:39 +0900
description: After installation of OneSpin
category: [EDA, Installation]
tags: [Questa, Onespin]
pin: false
math: true
mermaid: true
---

## One Spin 360 설치 후

OneSpin 360 설치 후 아래와 같이 환경 변수 추가 설정이 필요하다.

### Siemens EDA 의 flexnet License 사용할 경우
  
```text
 OSS_LICENSE_MODE  mgls
```
{: .nolineno }

### 제품 설치 경로 PATH 추가
  
```text
  QOSF_ROOT    C:/SiemensEDA/QOSF_2024.1    
  (본인 PC의 Questa Formal 제품군 설치 경로)

 ONESPINROOT  C:/SiemensEDA/QOSF_2024.1/onespin
  (본인 PC의 OneSpin 설치 경로)      
```
{: .nolineno }
