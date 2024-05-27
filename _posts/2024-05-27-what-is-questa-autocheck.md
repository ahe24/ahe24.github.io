---
layout: post
title: What is Questa AutoCheck
date: 2024-05-27 11:18 +0900
description:
category: [EDA, Formal]
tags: [Questa, Autocheck]
pin: false
math: true
mermaid: true
---

## :ballot_box_with_check: Questa Autocheck 소개

* Questa AutoCheck는 Formal 기반 버그 사냥 Tool 입니다. 이 툴의 최적 사용 시점은 블록 수준 검증이므로 설계자와 검증 엔지니어가 설계 및 검증 과정 초기에 사용하기에 적합합니다.

* Autocheck은 블록 내 버그 수를 최소화하고 자동화된 방식으로 가능한 쉽게 수행하는 것을 목표로 다음의 세 가지 설계 영역에서 버그를 찾는 푸시 버튼 방식의 툴입니다.

### :microscope: Autocheck 검증 영역

* RTL 수준 버그 : 시뮬레이션과 합성 불일치 (클럭 지연 등)
* Netlist 수준 버그 : Netlist 특정 구성 요소 (Combinational Loop, Bus conflict 등)
* Functional 수준 버그 : 순차적 로직에 대한 복합적인 기능적 버그 (Dead Code, Deadlock 등)

## :computer: Questa AutoCheck GUI

* :point_down: 아래 그림과 같이 테스트벤치 없이도 코드를 분석하여 기능적 잠재 오류 검출하여 해당 코드 및 회로 구조를 연동하여 보여준다.

![Questa AutoCheck GUI](</assets/img/240527/240527_ac1.png>)
