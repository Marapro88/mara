---
layout: post
permalink: /app-push-marketing-1/
title: '[디지털마케팅]앱 푸시 마케팅 3W(Who, When, What)_1편'
date: 2020-10-04 12:00:00 +09:00
feature: '/img/posts/11/01_T.jpg'
background: '/img/posts/11/01_B.jpg'
categories:
  - marketing
tags:
  - 스타트업
  - 디지털마케팅
  - 마케팅
  - 서버
  - 클라이언트
  - Braze 
  - 앱 푸시 마케팅
  - 앱푸시
  - 일잘러
  - 프로이직러
  - 프로이직러 Mara
description: 'Who-이벤트 활용해서 타겟 설정하기'
content_id: '1010'
---

안녕하세요~!<br>
프로이직러 Mara입니다.

오늘은 앱 마케터라면 반드시 알아야 하는 앱 푸시 마케팅을 할 때 고려해야 할 것들에 대해 알아볼게요. 

#### 0. 푸시 마케팅이란?

앱 마케팅은 크게 두 축으로 나눠서 생각해볼 수 있습니다. 신규 유저를 설득해서 우리 앱을 인스톨시키는 Acquisition 파트와 기존 앱 설치 유저가 서비스를 더 많이 이용하게 끔 하는 Retention이 바로 두 축인데요. 푸시 마케팅은 바로 retention에 해당합니다. 이미 앱을 인스톨한 유저를 대상으로 노티피케이션 바에 푸시 메시지를 노출시키는 거죠. 그리고 이 푸시 메시지를 자동으로 보내주고 통계 데이터도 제공해주는 툴이 푸시 마케팅 툴입니다. 시장에서는 마케팅 자동화 툴이라는 용어로도 부릅니다. 대표적인 툴로 Braze 같은 것이 있습니다. 그런데 푸시 메시지를 셋팅을 할 때 점검할 수 있는 체크리스트가 있으면 좋을 것 같은데요. 이럴 때는 보내려고 하는 푸시 메시지의 3W를 생각해보면 필요한 내용을 빠드리지 않고 좀 더 뾰족한 메시지를 쓸 수 있습니다.

- Who(누구)

- When(언제)

- What(무엇) 

이번 포스팅에서는 누구(Who)에 대한 내용과 이와 아주 연관이 깊은 이벤트의 개념에 대해서 다뤄보겠습니다. 

#### 1. Who: 누구에게 보낼 것인가?

#### 1-1. 타겟 유저가 누구인가?

메시지를 보낼 타겟 유저를 정하려면 유저 퍼널을 생각해보면 도움이 됩니다. 유저 퍼널은 유저가 앱에 접속한 시점부터 궁극적인 목적인 '구매'를 달성하기까지 거쳐야 하는 여정을 단계별로 정의하는 것을 의미합니다. 예를 들어 마켓컬리의 유저 퍼널은 '**앱오픈-상품조회- 장바구니-구매'** 가 되는 겁니다. 앱 퍼널의 깊은 단계까지 관여할 수록 서비스에 더 관심이 많은 유저이고 이를 앱과 상호작용이 높았다고 해서 '인게이지먼트가 높았다'라고 표현하기도 합니다. 타겟 유저를 정할때 서비스의 퍼널을 떠올려 보고 인게이지먼트 정도에 따라 타겟팅 우선순위를 조정하면 됩니다. 아무래도 앱 오픈만 한 유저보다는 장바구니 액션까지 한 유저가 결제를 유도하기 더 쉽겠죠? 

#### 1-2. 이벤트 정의하고 개발팀에 이벤트 생성 요청하기

위의 단계에서 퍼널을 정의하면 각 퍼널마다 유저가 해당 퍼널에 도달했다는 증거를 푸시 마케팅 툴에게 알려줘야 합니다. 마케팅에서는 이것을 '서버로 이벤트를 전송한다.' 라고 하는데요, 왜 이걸 마케터가 일일이 정의해줘야 할까요? 우리 서비스에 꼭 맞는 퍼널은 푸시 마케팅 툴이 알 수 없기 때문입니다. 마케팅 툴에서 해줄 수 있는 건 '앱이라면 응당 이런 이벤트는 발생하지!' 라고 상식적으로 정의할 수 있는 이벤트만 만들어 줄 수 있어요. (예를 들자면 앱오픈, 홈 화면 조회 정도) 그 이외 앱 내에서 유저가 하는 행동은 제공하는 서비스에 따라 완전히 다른 퍼널을 갖습니다. 카카오뱅크와 마켓컬리에서 정의하는 구매와 구매에 이르기까지의 여정이 완전히 다른것처럼요. 

#### 1-3. 이벤트의 종류

푸시 마케팅 툴에서 사용 할 수 있는 이벤트의 종류는 크게 2가지로 구분됩니다. 

- 실시간 이벤트 
  - 클라이언트 이벤트 
  - 서버 이벤트 

- 데이터 기반 이벤트

실시간성 이벤트는 말그대로 유저 행위에 기반한 실시간 이벤트를 의미합니다. '지금 결제 버튼을 클릭한 유저'와 같은 이벤트가 실시간 이벤트입니다. Braze에서는 이것을 Custom event 라는 용어로 표현합니다. 실시간으로 유저 행동을 알아야 하기 때문에 이벤트 소스는 서버가 됩니다. 실시간성 이벤트는 다시 한번 클라이언트 이벤트와 서버 이벤트로 구분됩니다. 보통 페이지 조회, 클릭과 같이 앱 UI상에서 유저가 일으키는 액션에 대한 이벤트는 클라이언트 팀에서 지원완료, 구매완료 액션에 대한 결과값을 판단하는 이벤트는 서버 팀에서 처리해줍니다. 그래도 헷갈리신다면 생성하고 싶은 이벤트의 정의를 개발자에게 설명하고 담당 부서를 문의하시면 됩니다. 

반면에 유저가 지금까지 앱과 상호작용한 히스토리에 근거한 이벤트는 데이터 기반 이벤트 입니다. '지금까지 결제를 3번 이상한 유저'와 같은 이벤트가 데이터 기반 이벤트입니다. Braze에서는 이것을 Custom attribute라는 용어로 표현합니다. 이벤트를 가져오는 소스도 (당연하지만)데이터베이스 입니다. 만약에 내가 원하는 이벤트를 데이터로 쌓지 않고 있는 경우 데이터를 관리하는 팀과 상의해서 해당 데이터를 DB에 적재하는 일부터 진행해야 합니다. 데이터 기반 이벤트를 타겟팅 목적으로 사용할 때 유의해야 할 점은 기간기준을 함께 고려해야 하는 부분입니다. 구매완료를 3회 이상한 유저라고만 타겟팅을 걸어버리면 일년 동안 3회 이상 구매한 유저와 한달 동안 3회 이상 구매한 유저가 동일한 타겟팅 그룹으로 묶이게 됩니다. 둘은 실제로는 굉장히 다른 성격의 유저임에도 말이죠. 

그럼 둘 중에 어떤 이벤트를 사용해야 할 까요? <br>
메시지를 보내는 목적에 따라서 달라지게 됩니다. 유저의 앱 내 행동에 따라 실시간으로 메시지를 보내고 싶은 경우에는 실시간 이벤트에 기반해 타겟팅을 해야 하는 반면에 특정 행동 패턴을 보인 유저를 발라내서 타겟팅을 하고 싶은 경우 데이터에 이벤트를 활용해서 푸시를 셋팅하면 됩니다. 예를 들어서 실시간 이벤트로 가장 기본적으로 시도해볼 수 있는 조합은 다음 단계 퍼널은 완료하지 않았지만 이전 단계 퍼널은 완료한 유저 조합입니다. 장바구니에 상품을 담았지만 구매는 완료하지 않았거나 상품은 조회했지만 장바구니에 담지 않은 유저에게 다음 단계를 완료하라는 메시지를 보내볼 수 있습니다. 반면에 최근 한 달이내 구매완료 3회 이상 유저를 서비스에서 충성유저로 정의했다면 해당 유저만을 위한 프로모션을 기획해서 푸시 메시지를 보내볼 수 있습니다.<br>
위의 내용을 표로 정리하면 아래와 같습니다.  

![이미지1](/img/posts/11/1.JPG)

오늘은 앱 푸시 마케팅을 할 때 고려해야 할 것들 중 Who에 해당하는 타겟 유저와 이벤트에 대해서 살펴보았습니다. 다음 글에서는 When과 What에 해당하는 발송 시점과 메시지 콘텐츠에 대해 다뤄보겠습니다.<br>오늘도 칼퇴하세요 ~!  🙋‍♀️

**✅서버/클라이언트 개념을 모르겠다면👉** [글 보러 가기](https://mara.kim/marketing-cheat-key-3-dev-knowledge/)<br>
**✅Braze로 캠페인 생성하는 방법이 궁금하다면👉** [글 보러가기](https://mara.kim/marketing-braze-honey-tip2-campaign-setting/)