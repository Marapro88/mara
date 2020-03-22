---
layout: post
permalink: /braze-honeytip1-target-user/
title: 'Braze 사용 꿀팁1_Target User 생성'
date: 2020-03-14 10:30:00 +09:00
feature: '/img/posts/02/02_Thumnail.png'
background: '/img/posts/02/01_Back.jpg'
categories:
  - marketing
tags:
  - 스타트업
  - 밸런스히어로
  - 마케팅
  - 핀테크
  - braze
description: 'Segments 기능 활용해서 도달가능 유저 확인하는 꿀팁'
---

안녕하세요~! 

프로이직러 Mara입니다.🐳

입사 첫날, Mara가 하게 된 업무는 Braze를 통해서 Push Message를 보낸 것이었습니다. 첫날이어서 정신이 없는데 처음 보는 마케팅 툴을 다루려니 식은땀이 나더라고요. Mara처럼 Braze를 처음 접하는 마케터가 참고하실 수 있도록 핵심적이고 유용한 내용 위주로 작성해볼게요.

## Braze란?

우선 Braze가 뭔지 간단하게 알아볼까요?

Braze는 마케팅 자동화 솔루션으로서 기존의 마케터들이 이메일, SMS, 카카오톡, 인앱메시지 등 다양한 채널을 통해 고객들에게 전달했던 마케팅 메시지를 자동화하여 마케터가 원하는 시점, 원하는 조건에 자동으로 메시지를 전달합니다.

|출처: AB180 블로그

Braze를 활용한 마케팅 메시지 작성은 크게 3단계를 거칩니다.

1. Target User 생성
2. Campaign 생성
3. Campaign 성과측정

이번글에서는 Target User 생성과 관련된 내용을 다뤄볼게요. 마케팅 메시지를 발송하려면 우선 메시지를 받을 고객 즉, Target User를 정의해야 합니다. Braze에서는 Target User를 정의하는 방법을 3가지로 제공하고 있는데요. 한 가지씩 살펴볼게요.

- Custom Event(Event base)

Target User가 우리 서비스, 앱내에서 특정 행동을 하는 순간 또는 이후에 마케팅 메시지를 전달하고 싶을 때 Custome Event(줄여서 CE)를 사용합니다. 예를 들면 대출을 받으려고 시도했다가 'Rejected'를 받은 순간에 다른 상품을 추천하는 메시지를 쏘는 식으로 활용하는 거죠. CE는 Target User로도 활용하지만 캠페인의 성과측정 목적으로도 활용할 수 있습니다.

- Custom Attribute(Attribute base)

앱내에서 이미 특정 행동을 한 유저를 Target User로 삼고 싶을 때 Custom Attribute(줄여서 CA)를 사용합니다. 예를 들면 대출 경험이 2회 이상인 유저를 대상으로 메시지를 쏘고 싶을 때 활용합니다.

- User base

위의 2가지 Custom Filter를 활용하면 실시간으로 원하는 조건에 해당하는 유저를 대상으로 메시지를 발송할 수 있습니다. 하지만 Custom 이라는 단어에서 짐작할 수 있듯이 braze에서 제공되는 것이 아니라 고객 스스로 자사 서비스에 맞게 개인화해서 생성해야 한다는 거죠. Custom Event는 서버 개발자가 Custom Attribute는 데이터 팀(다른 회사에서는 어디로 요청을 하는지 모르겠네요)으로 요청을 해서 만들어줘야 합니다. 하지만 타깃 유저를 정의하고 매번 리소스를 투입해서 만들 수는 없습니다. 또는 앱이 버전 업그레이드를 하면서 신규 서비스가 론칭되면 미처 CA, CE가 개발되어 있지 않을 수도 있죠. 이럴 때는 User list를 직접 CSV 파일 형식으로 받아서 User import라는 기능을 활용해 직접 Segment를 생성하면 됩니다.

## User Import 주의사항

User Import를 정상적으로 실행하기 위한 몇 가지 주의사항이 있습니다.

· 파일형식은 CSV 일 것

· 칼럼 제목은 External_id를 사용할 것(대소문자 구분)

· braze_id 를 추출해서 올릴 것 (고객의 전화번호 또는 내부 DB에서 관리하는 key값(예를 들면 User_id)에 맵핑된 braze_id를 추출해서 올려야 합니다)

## Segment 기능 활용 꿀팁

이렇게 생성한 Segment의 모수는 실제로 메시지를 발송해서 도달할 수 있는 유저수(Reachable user)와 다를 수 있습니다.

크게 두 가지 이유 때문인데요,

1. Push 기능을 Off 한 유저
2. App Uninstall 한 유저

어떤 이유로 얼마나 gap이 나는 지 확인할 수 있는 방법이 있습니다. Braze에서 제공하는 Segments 대시보드를 이용하면 됩니다.

![이미지1](/img/posts/02/01.png)

![이미지2](/img/posts/02/02.png)

![이미지3](/img/posts/02/03.png)

![이미지4](/img/posts/02/04.png)

![이미지5](/img/posts/02/05.png)

위 순서대로 Segment기능을 활용해서 User import를 통해 생성한 Segment를 모수로 두고 Push enabled is true, Has not uninstalled 두 가지 조건을 차례로 걸면 Reachable User와의 gap을 확인할 수 있습니다. 이번 글에서는 braze가 무엇인지, 메시지를 받을 Target user를 정의하는 Segment를 어떻게 생성하는지에 대해 알아봤습니다.

다음 글에서는 braze를 통해서 캠페인을 생성하는 방법을 알아볼게요! 

오늘도 칼퇴하세요 ~!😀