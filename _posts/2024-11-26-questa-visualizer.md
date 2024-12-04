---
layout: post
title: QuestaSim Visualizer 활용
date: 2024-11-26 10:27 +0900
description: QuestaSim의 새로운 GUI인 Visualizer를 사용하는 방법
image:
  path: /assets/img/241126/vis_wave.png
  alt: visualizer 실행 화면  
category: [EDA, Simulation]
tags: [Questa, visualizer]
pin: false
math: true
mermaid: true
---

## QuestaSim Visualizer 활용

`Modelsim`/`QuestaSim`을 사용해 본 사람들이라면 타사 툴인 `Verdi`, `SimVision` 과 같은 waveform 디버거에 비해 디자인이나 기능적인 면에서 불편함이나 부족함을 경험해본 사람들이 많을 것이다.

최근, `Mentor Graphics`를 인수한 `Siemens EDA`에서 `QuestaSim` 2023.1 버전 이상부터 파격적으로 디자인, 기능 및 성능을 업그레이드한 `Visualizer`란 Advanced Debug 환경을 제공하고 있다.

실제 작업 중인 개발 프로젝트에서 새로 나온 `Visualizer`를 직접 활용해 보니 여러모로 효율적인 디버깅이 가능하여 꽤 성공적인 개발 환경을 경험하게 되었다.

이에, 본인이 습득한 최적의 `visualizer` 활용법을 공유하고자 한다.

### Windows 운영체제에서 Questa Visualizer 실행 환경 설정

리눅스는 기본적으로 `bash`나 `csh` 이 있어서 스크립트 기반으로 툴을 사용하는 것이 자연스럽고 당연한 일이지만 윈도우즈 환경에서 제공하는 명령창이나 `powershell`은 불편함이 많다.
그래서, 리눅스 명령을 윈도우즈에서도 사용할 수 있도록 `cygwin`이나 `WSL`을 추가 설치하거나 버전관리를 위해 `git`을 설치하면 `git-bash` 환경을 윈도우즈에서 활용할 수 있다.

가장 선호하는 쉘 터미널 환경을 자신의 윈도우즈에 구축하기 바란다. 본인은 `git`을 자주 사용하기에 같이 설치된 `git-bash`를 주로 사용한다.

또한, 윈도우즈에서 리눅스 쉘 환경을 사용시, 명령 스크립트 자동화를 위한 강력한 툴인 `Make`를 좀 더 편하게 활용할 수 있는데 윈도우즈에서 `Make`를 설치하는 방법은 각종 블로그에 잘 소개되어 있으니 참고해서 꼭 설치하기를 권장한다.

아래와 같이 vscode 사용자라면 터미널을 IDE에 배치하여 사용하면 작업시 여러 창을 왔다갔다 할 필요없이 하나의 IDE에서 대부분의 작업을 할 수 있어 매우 편리하다.

![alt text](/assets/img/241126/vscode_ide.png)

### Makefile 구성

아래와 같이 간단하게 로직 시뮬레이션용 컴파일 명령들을 `Makefile`로 구성하여 명령쉘에서 수행하면 반복 테스트시 편리하게 사용할 수 있으며, 다른 프로젝트에서도 소스파일 리스트만 수정하는 방식으로 빠르게 구성하여 활용할 수 있다.

```make
# sources
REFSRC ?= ../netlist/top_normal.v
TBSRC  ?= ../testbench/tb_net.sv clk_wiz_0_sim_netlist.v
#Simulation TOP module name
TOP = tb_net glbl
#SIM LIBRARY list for OPT
OPT_ARGS = vopt_args.f
# Make Targets
all: compile opt sim

create_lib:
  vlib work

#compile: create_lib vcom_compile vlog_compile 
compile: create_lib vlog_compile 

vlog_compile:
  vlog -sv $(REFSRC) 
  vlog -sv $(TBSRC) 

opt:
  vopt $(TOP) -o opt -f $(OPT_ARGS) -debug -designfile design.bin

sim:
  vsim -c opt -do "run -all; quit -f" -qwavedb=+signal+wavefile=qwave.db

vis_wave vw:
  vis -designfile design.bin -wavefile qwave.db &

```

### Makefile을 통한 simulation 수행

아래와 같이 `vscode` 터미널에서 `make` 명령을 통해 스크립트를 실행하면 매우 편리하다.

![alt text](/assets/img/241126/241205_081814.gif)

### Visualizer 실행하여 waveform debugging

다음과 같이 `visualizer` 실행시 필요한 `design.bin` 파일과 `qwave.db` 파일을 실행하는 명령도 미리 `Makefile`에 정의해 두면 빠르게 실행이 가능하다.

![alt text](/assets/img/241126/241205083123.gif)
