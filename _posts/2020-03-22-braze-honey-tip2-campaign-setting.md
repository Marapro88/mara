---
layout: post
permalink: /marketing-braze-honey-tip2-campaign-setting/
title: 'Braze 사용 꿀팁 2_Campaign 생성하기 '
date: 2020-03-22 14:00:00 +09:00
feature: '/img/posts/03/02_Thumnail.jpg'
background: '/img/posts/03/01_Back.jpg'
categories:
  - marketing
tags:
  - 스타트업
  - 밸런스히어로
  - 마케팅
  - 핀테크
  - Braze
description: 'Braze 활용해서 서비스 유저에게 Push/In-app message보내는 방법'
---

안녕하세요~!<br>
프로이직러 Mara입니다. 

이전 글에서는 우리 제품을 마케팅하고 싶은 대상인 Target user를 생성해봤습니다. 이제 Target user를 대상으로 마케팅 메시지를 전달하기 위해서 캠페인을 설정하는 방법에 대해서 알아볼게요. Braze에서는 보낼 수 있는 메시지 종류가 여러 가지 있지만 Mara가 주로 사용한 Push를 세팅하는 방법을 다뤄보겠습니다. 

## Push vs In-app message
우선 글을 시작하기에 앞서서 Push 와 In-app message가 무엇인지 살펴볼게요. 

![이미지1](/img/posts/03/01.png)![이미지3](/img/posts/03/03.png)

위 2개 이미지 중 좌측 이미지가 Push 우측 이미지가 In-app message입니다. Push는 모바일 잠금 화면 또는 알림 센터에 발송되는 메시지를 말합니다. In-app message는 서비스 앱 내에서 서비스 이용 중에 발송되는 메시지로 Braze에서는 3가지 type의 In-app message를 제공하고 있습니다.

![이미지4](/img/posts/03/04.png) 

## Campaign 세팅하기 

![이미지5](/img/posts/03/05.png)

### Step 1. Create new campaign

1. 좌측 메뉴바에서 ‘Campaigns’를 클릭
2. +Create campaign 클릭
3. 발송하고자 하는 메시지 type선택

### Step2. Compose

![이미지6](/img/posts/03/06.png)

1. Campaign 이름입력 
2. 1개의 Campaign에서 여러 가지 Message를 Test 해보고 싶은 경우 Add variant를 눌러서 Variant별로 다른 메시지를 작성할 수 있다
3. Variant 명 입력
4. Push Title/Message 입력하기
5. User customized 메시지 입력을 위해 +버튼 누르기

## 꿀팁1- 개인화 메시지 보내기 

![이미지7](/img/posts/03/07.PNG)

메시지 입력창에서 “+”버튼을 누르고 들어가면 메시지를 개인화할 수 있는 창이 나옵니다. 이 기능을 사용하면 사내 DB에 저장되고 있는 유저의 정보를 활용해서 개인에게 맞춤화된 메시지를 발송할 수 있습니다.

* Personalization Type

여기서 어떤 값을 선택하느냐에 따라서 사용할 수 있는 Attribute의 종류가 결정됩니다. Braze에서 기본적으로 제공하는 Type은 Default attributes입니다.

* Attribute

이름, 이메일, 성별, 마지막으로 앱 업데이트를 한 시점 등등 유저의 정보를 활용하여 개인에게 맞춤화된 메시지를 제공할 수 있습니다. 유저의 이름인 first_name을 골라보았습니다.

* Default value(optional)

특정 유저가 Attribute에서 선택한 정보의 값을 가지고 있지 않은 경우, default로 보여줄 값을 입력해줍니다. “User”를 입력합니다.

* Preview

실제 유저가 메시지를 받았을 때 볼 화면을 미리 보여줍니다.

![이미지8](/img/posts/03/08.png)

1. 이미지 삽입하기 

   이미지를 삽입할 때 유의할 점은 메시지 type에 따라서 권장하는 이미지 spec이 있습니다. 권고 스펙은 이미지 삽입하는 pop-up창에서 안내해주고요, Push의 경우는 2:1 ratio를 반드시 지켜야만 올릴 수 있습니다. 2:1 비율이 아닌 이미지도 ‘Only images with a 2:1 aspect ratio.’ 체크박스를 해제하면 화면에 표시는 되지만 최종 삽입은 되지 않습니다. 

    ![이미지9](/img/posts/03/09.PNG)

2. On click behavior 
   유저가 푸시 메시지를 클릭했을 때 일어나는 행동을 지정해줍니다. 

* Open App

* Redirect to Web url

* Deep Link into Application 

  3가지 행동 type을 제공하지만 유저의 engagement를 높이기 위해서는 Deep Link를 통해서 유저가 engagement를 일으키기를 원하는 그 페이지에 랜딩 시켜주는 것이 중요하겠죠. Deep link는 Product 팀과 상의해서 미리 개발되어 있는 경우는 Deep Link를 받아서 사용하면 되고 없는 경우에는 담당자에게 개발해달라고 요청하셔야 합니다. 

3. Device options 
   유저가 Multi-device를 사용하는 경우 가장 최근에 사용한 device에만 푸시 메시지를 보내주는 기능입니다. 국가에 따라서는 개인이 여러 대의 단말기를 사용하는 경우가 일반적인 경우가 있기 때문에 이 옵션을 체크하기를 추천합니다.

### Step 3. Delivery

![이미지10](/img/posts/03/10.PNG)

메시지 발송 시점은 주로 2가지를 사용합니다. 

1. Scheduled Delivery

* Send at a Designated time
   우리말로 하면 예약 발송 정도 되겠네요.
   어느 정도의 주기로 시간과 요일, 반복 횟수 등을 지정할 수 있습니다.

* Intelligent Delivery
   지정된 시간이 아닌 Braze가 판단하에 유저가 가장 engage할 가능성이 높은 시간대에 발송을 해주는 기능입니다. 다만 유저가 다수의 캠페인에 해당 delivery옵션으로 타기팅되어 있을 경우 복수의 메시지를 한꺼번에 받을 수 있습니다.

2. Action-Based delivery 
   유저가 특정 행동을 행한 시점에 메시지를 발송할 수 있는 기능입니다. 
   구매한 직후, 앱을 연 시점에서 5초 경과 후, Target user를 목적으로 만든 CE 이벤트 등을 활용할 수 있습니다. 

## 꿀팁2-메시지 반복 시점 정의하기 


Delivery 영역 제일 하단에 위치한 'Delivery control'은 정기적으로 반복되는 메시지를 세팅한 경우 수신 자수를 컨트롤하는 기능입니다. 여기서  ‘Allow users to become re-eligible to receive campaign’ 체크박스를 활성화 시킨 후 1 day로 세팅해두면 메시지를 수신한 이후 1일 경과 후 다시 메시지 수신 대상자가 된다는 의미입니다. 만약 매일 발송되는 푸쉬 메시지를 예약해두고 re-eligible을 설정하지 않거나 발송 주기보다 re-eligible period를 1일 이상으로 설정 해두면 유저가 매일 메시지를 받아볼 수 없으므로 발송하고자 하는 주기에 맞게 re-eligible기간을 설정 하는 것 잊지 말아주세요!

![이미지11](/img/posts/03/11.png) 

오늘도 칼퇴하세요 ~! 🙋‍♀️