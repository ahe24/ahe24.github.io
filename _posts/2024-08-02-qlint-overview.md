---
layout: post
title: What is Questa Lint?
date: 2024-08-02 08:29 +0900
description: Questa Lint 소개
category: [EDA, Formal]
tags: [Questa, Lint, DO-254, ISO-26262]
pin: false
math: true
mermaid: true
---

## RTL 코드에 대한 정적 분석 툴

- Identify/fix the issues as RTL is created/evolves
  - Reduces wasted iterations
  - Improves design efficiency
  - Lint is a static tool - requires no stimulus or constraints
    - Fast, requires no input apart from RTL
- Improve quality of RTL by following corporate (and industry standard) coding guidelines
- Ensure RTL is re-usable

> 테스트 벤치나 contraints 가 필요 없음
{: .prompt-tip }

## 특징

```mermaid

block-beta
  columns 2
  block:group1
    columns 1
    a(["Syntactic"]) a1["Is the code 
    properly constructed?"]
    
  end
  block:group2
    columns 1
    b(["Semantic"]) b1["Do the elements
    make contextual sense?
    "]
  end
  block:group3
    columns 1
    c(["Stylistic"]) c1["Is the code properly named, commented
     and laid out to meet requirements?"]
  end  
  block:group4
    columns 1
    d(["Structural"]) d1["Do the pieces form 
    a coherent whole?"]
  end  

style a fill:#8bc0c7;
style b fill:#8bc0c7;
style c fill:#8bc0c7;
style d fill:#8bc0c7;

```

## Questa Lint WorkFlow

![alt text](/assets/img/240802/qlintflow.png)

## Questa Lint - Types of Methodologies

![alt text](/assets/img/240802/qlint_metho.png)

> Lint 검사에 대한 표준 설정이 가능하다.
> ISO-26262, DO-254 같은 인증이 필요한 프로젝트 진행시
> 코드 리뷰 결과 산출물이 요구되는 경우 이에 적합한 다양한 코딩 룰 설정이 가능하다.
{: .prompt-tip }
