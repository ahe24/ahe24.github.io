---
layout: post
title: What is Questa CDC
date: 2024-08-12 08:22 +0900
description: Questa CDC 소개
category: [EDA, Formal]
tags: [Questa, CDC, metastability]
pin: false
math: true
mermaid: true
---

## :ballot_box_with_check: Clock-Domain Crossing (CDC)란 무슨 의미?

- 비동기 클록 도메인:

  - 다른 도메인과의 클록 위상 관계가 변동적이거나 예측 불가능한 레지스터를 포함.
  
- CDC(Cross-Domain Clock) 신호:
  - 하나의 클록 도메인에서 시작됨.
  - 다른 클록 도메인의 레지스터에 의해 샘플링 됨.

> 현대 SoC 단일 칩에서 10,000개 이상의 CDC 신호를 가질 수 있슴.
{: .prompt-tip }

## :ballot_box_with_check: 왜 CDC Error는 치명적일까?

- 보통 Simulation 단계에서 발견되지 않음
- 개발단계 후반, 그리고 종종 chip 레벨 또는 보드 실장 테스트에 이르러서야 발견됨

## :ballot_box_with_check: Chip 레벨에서의 결함

- 결함에 대한 재현이 어렵다.
- 디버깅 또한 쉽지 않다.

## :ballot_box_with_check: CDC 경로는Metastability를 야기한다

- CDC(Cross-Domain Clock) 신호가 수신 도메인의 레지스터의 Setup time이나 Hold time 사이에 값이 변할 때 수신 레지스터는 메타스테이블 상태가 될 수 있다.
  - 메타스테이블 상태는 예측할 수 없는 시간 후에 임의의 값으로 설정됨
  - 적절한 동기화 및 프로토콜을 사용하더라도 발생할 수 있다
  - 이로 인해 설계에서 심각한 기능적 문제가 발생할 수 있다

![alt text](/assets/img/240812/meta_soc.png)

## :ballot_box_with_check: Questa CDC 를 통한 검증

- CDC Structural Verification
  - Verify CDC synchronization structures
- CDC Protocol Verification
  - Protocols are specific to synchronization structures
- CDC Reconvergence Verification
  - Reconvergence requires correct synchronization

## :ballot_box_with_check: Questa CDC GUI

![alt text](/assets/img/240812/quest_cdc_gui.png)
