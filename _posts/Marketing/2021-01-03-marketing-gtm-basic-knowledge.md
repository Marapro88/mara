---
layout: post
permalink: /gtm-0-basic-knowledge/
title: '[디지털마케팅]마케터의 GTM활용 가이드_1편'
date: 2021-01-03 12:00:00 +09:00
feature: '/img/posts/15/01_T.jpg'
background: '/img/posts/15/01_B.jpg'
categories:
  - marketing
tags:
  - 스타트업
  - 디지털마케팅
  - 마케팅
  - GTM
  - 전환태그
  - 트리거  
  - 맞춤 이벤트
  - 변수
  - 사용자정의변수
  - 데이터영역변수
  - GTM Tag
  - GTM Trigger
  - GTM Variable
  - Data Layer
  - 일잘러
  - 프로이직러
  - 프로이직러 Mara
description: 'GTM 활용에 필요한 기초지식 '
---

안녕하세요~!<br>
프로이직러 Mara입니다.

구글에서는 마케터의 데이터 분석을 돕는 여러가지 마케팅 플랫폼을 제공하는데요. 구글 마케팅 플랫폼 중 하나인 GTM에 대해서 마케터 활용 가이드를 총 4 단계에 걸쳐서 포스팅 해보려고 합니다. GTM을 공부하면서 아쉬웠던 점은 GTM 을 통해서 마케터가 어떤 분석을 할 수 있고 궁극적으로 데이터 분석 플랫폼이나 광고 플랫폼과 어떻게 연결 되는 지 설명하는 자료가 많이 없는 점이었어요. 뒤에서 설명하겠지만 GTM 은 데이터 분석이나 광고를 더 잘 하기 위한 수단이거든요. 그래서 직접 이것 저것 셋팅해보면서 자료를 포스팅할 예정입니다. 아래의 순서로 포스팅 할 예정이니 목차를 보고 필요한 내용만 취사 선택해서 보셔도 좋아요!   

0.GTM 기초

- GTM이란? 
- GTM 구성요소 정의 
- GTM 구성요소 간의 상관관계
- GTM 내의 Event

1.GTM Data Layer

- Data Layer(데이터 영역변수)정의
- Variable에서 데이터 영역 변수 활용법 
- Trigger에서 데이터 영역 변수 활용법 
- Tag에서 데이터 영역 변수 활용법
- Variable vs Data Layer

2.GTM App Event 셋팅법

- TBD

3.GTM 미리보기 활용 꿀팁

- TBD

4.마케터의 GTM 활용법 

- TBD

#### 0. GTM이란?

GTM은 Google Tag Manager의 약자입니다. 마케터는 웹과 앱에서 유저가 발생시키는 액션을 트래킹하고 싶은 니즈가 있습니다. 대표적으로 전환 이벤트에 대한 정보를 알면 마케팅 하는 데 도움이 되겠죠. 기존에는 개발자 도움을 받아 이벤트 추적 script 를 소스 코드에 직접 추가해야 했습니다. GTM은 개발자의 도움 없이 이벤트 트래킹 tag를 심을 수 있는 구글 마케팅 플랫폼입니다. 

#### 1. GTM 구성요소 정의

GTM은 크게 Variable, Trigger, Tag 라는 3가지 구성 요소로 이루어져 있습니다. 

각 구성요소에 대한 정의를 구글에서 가져와봤습니다. 

- Variable :  제품 이름, 가격 값 또는 날짜와 같이 변경 될 값에 대한 지정 값(named placeholder) 입니다. 
- Trigger : 트리거는 클릭, 양식 제출 또는 페이지로드와 같은 특정 이벤트를 수신합니다. 트리거 정의와 일치하는 이벤트가 감지되면 해당 트리거를 참조하는 모든 태그가 실행됩니다. 
- Tag : Google Analytics와 같은 시스템에 데이터를 보내는 코드입니다. 

#### 2. GTM 구성요소 간의 상관관계

Tag, Trigger, Variable 세가지 구성요소가 유기적으로 연결되어 우리가 원하는 유저 액션을 트래킹 할 수 있습니다. 구성요소간의 상관관계에 대해서 알아볼게요. 

- **Tag와 Trigger** 

Tag는 웹이나 앱에서 유저 행동을 트래킹하는 코드 조각입니다. GTM Tag는 유저 행동을 측정해서 3rd party(Google Analytics, Google Ads, Facebook 등등)에 전달해주는 역할을 합니다. GTM은 UI를 살펴보시면 아시겠지만 데이터 분석 기능은 제공하지 않습니다. Tag를 셋팅할 수 있을 뿐이죠. 그래서 꼭 데이터 분석 플랫폼, 광고 플랫폼과 연동해서 사용해야 합니다. 물론 GTM에서는 간단하게 GA, Facebook 분석 스크립트를 삽입하는 기능을 제공하고 있습니다. 자세한 방법은 구글링 해보세요! 

그럼 Tag와 Trigger는 어떤 상관관계를 가질까요? <br>Tag는 이벤트 발생 순간을 감지하고 동작합니다. 이때 어떤 event에 반응 할 지를 정의하는 것이 Trigger 입니다. 그래서 GTM에서 Tag를 셋팅할 때 반드시 Trigger를 설정하도록 UI 가 구성되어 있어요. 복잡하게 설명했지만 'Trigger가 Tag가 동작하는 시점을 정의한다' 라고 이해하면 됩니다. 

- **Trigger와 Variable** 

GTM은 기본 제공 변수(built-in variable)와 함께 사용자 정의 변수(custom variable)을 제공합니다. 변수는 원하는 정보를 Tag에 전달할 뿐만 아니라 Trigger 의 필터 조건으로 활용 할 수 있습니다. 예시와 함께 설명해볼게요.

여기서 활용한 event(ViewContent) 는 Data Layer를 활용해 '페이지 조회'시 작동하도록 미리 셋팅해둔 맞춤 이벤트입니다. 어떤 Tag가 전체 페이지 75%이상 읽었을 때 작동하는 Trigger를 만든다고 해볼게요. 이때 Trigger의 필터 조건에 사용된 Scroll Depth Threshold 가 변수이고 75%라는 변수의 값을 활용하여 셋팅할 수 있습니다. 만약 기본 제공 변수에 마케터가 원하는 변수가 없다면 사용자 정의 변수를 활용해서 변수를 추가할 수도 있습니다. 

- 이벤트 이름: ViewContent

- 트리거 유형: 맞춤 이벤트

- 트리거 실행: 일부 맞춤 이벤트 

- - 이벤트가 발생하고 모든 조건을 충족하는 경우 이 트리거 실행

    *Scroll Depth Threshold 75%이상 일 때만* 

![이미지1](/img/posts/15/01JPG)

![이미지2](/img/posts/15/02JPG)

- **Tag와 Variable** 

Variable은 가변적인 값을 추적하는 목적으로 Tag 안에서 사용 될 수도 있습니다. 대표적으로 전환 추적 Tag 에서 구매 제품의 가격처럼 동적으로 변하는 값을 추적해야 하는 경우 Variable을 사용할 수 있습니다. 

- **GTM 구성요소간의 상관관계** 

결과적으로 Trigger는 Variable을 포함하고 있고 Tag는 Trigger를 포함하고 있습니다. <br>
'Variable < Trigger < Tag 순서대로 상위 개념이고 하위 개념을 포함한다.' 라고 이해하시면 좋을 것 같아요. 

#### 3.GTM 내의 Event 

그런데 구성 요소를 살펴보니 궁금증이 생겼습니다. GTM 구성요소에는 Event가 없었어요!😮 Event는 그럼 어디서 만들까요? 이쯤에서 Trigger 의 정의를 다시 한번 살펴볼게요. 

Trigger : 트리거는 클릭, 양식 제출 또는 페이지로드와 같은 특정 `이벤트`를 수신합니다. 트리거 정의와 일치하는 `이벤트`가 감지되면 해당 트리거를 참조하는 모든 태그가 실행됩니다.

정의에서 반복해서 언급하는 것처럼 Trigger 가 동작하는 기준은 `이벤트` 입니다. Trigger 구성 화면을 눌러보면 트리거 유형에서 제공하는 페이지뷰, 클릭, 사용자 참여 등이 모두 GTM에서 기본적으로 제공하는 이벤트 입니다. 트리거 유형을 고르고 저장하면 최종적으로 이벤트 유형으로 표기되는 걸 확인할 수 있어요. 

![이미지3](/img/posts/15/03.jpg)

만약 기본 제공 이벤트에서 원하는 이벤트가 없는 경우는 `트리거 유형 > 맞춤 이벤트` 를 활용해서 맞춤 이벤트를 셋팅 할 수 있습니다. 사용자 정의 변수와 마찬가지로 맞춤 이벤트 또한 데이터 영역 변수를 활용해서 셋팅합니다. 이 내용도 다음글 Data Layer 활용편에서 다룰게요!  

![이미지4](/img/posts/15/04.jpg)

Trigger 유형 별 자세한 정의가 궁금하시다면 아래 구글 개발자 문서를 참조해주세요!<br>
[Trigger 유형 구글 개발자 문서](https://support.google.com/tagmanager/topic/7679108)

끝으로 GTM에서 제공하는 변수, 트리거, 태그 유형에 대해 잘 정리된 포스팅을 발견해서 공유합니다. 어떤 변수, 트리거 유형을 골라야 할 지 헷갈릴 때 찾아보면 정말 좋을 것 같아요! 

[evan-moon 블로그|GTM 뜯어보기](https://evan-moon.github.io/2020/04/19/what-is-gtm-google-tag-manager/)

오늘도 칼퇴하세요 ~!  🙋‍♀️

[참고문서 Component of Google Tag Manager ](https://support.google.com/tagmanager/answer/6103657?hl=en)

[참고문서 Variables - Tag Manager Help](https://support.google.com/tagmanager/topic/7683268?hl=en&ref_topic=3441647)

