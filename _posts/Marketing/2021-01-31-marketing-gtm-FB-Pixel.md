---
layout: post
permalink: /gtm-5-fb-pixel/
title: '[디지털마케팅]마케터의 GTM활용 가이드_5편'
date: 2021-01-23 12:00:00 +09:00
feature: '/img/posts/19/01_T.png'
background: '/img/posts/19/01_B.jpg'
categories:
  - marketing
tags:
  - 스타트업
  - 디지털마케팅
  - 마케팅
  - GTM
  - GTM FB Pixel 추가
  - GTM 페이스북 픽셀 추가
  - GTM 페이스북 이벤트
  - GTM 페이스북 이벤트 추가
  - GTM 페이스북 픽셀 설치
  - GTM 페이스북 Pixel 설치
  - GTM 페이스북 픽셀 파라미터 추가
  - GTM 페이스북 standard event
  - FB Standard event
  - FB Standard event parameter
  - FB custom event
  - 페이스북 커스텀이벤트
  - 페이스북 스텐다드 이벤트  
  - 일잘러
  - 프로이직러
  - 프로이직러 Mara
description: 'GTM 활용해서 FB Pixel로 Tag 전송하기'
content_id: '1018'
---

안녕하세요~!<br>
프로이직러 Mara입니다.

이번 포스팅은 GTM을 활용해서 FB Pixel로 이벤트와 변수를 전송하고 이를 모수로 활용해서 광고 운영하는 방법에 대해 포스팅해보겠습니다. 

[TOC]

#### 1. FB Pixel이란?

 Pixel은 웹사이트 HTML header section에 삽입하는 코드로 Pixel을 설치하면 웹내 유저 행동을 페이스북으로 전송할 수 있습니다. 페이스북은 이렇게 수집한 유저 행동 정보를 광고 모수로 활용 가능합니다. GTM에서 웹 사이트 별도 코드 수정 없이 GTM 만으로 Google Analytics에 이벤트를 전송했던 것처럼 FB Pixel에도 GTM을 활용해 이벤트와 변수를 전송할 수 있습니다. 다만 이 방식은 웹에서만 가능하고 앱은 FB SDK를 설치하고 개발자를 통해 직접 event 전송 코드를 작성해야 합니다. 

#### 2. FB 이벤트 종류

우선 FB Pixel에서 제공하는 이벤트의 종류는 크게 3가지 입니다. 

1. Standard Event 

   페이스북에서 미리 정의해둔 이벤트입니다. Standard Event중에 사용하고자 하는 이벤트가 있다면 해당 이벤트 명을 그대로 가져와서 사용하면 됩니다. 

2. Custom Event 

   Standard Event에서 활용하고 싶은 이벤트가 없는 경우 마케터가 스스로 이벤트명을 정하고 간단한 코드를 통해 custom event를 생성할 수 있습니다. 

3. Custom Conversion 

   Conversion를 활용해 광고 성과 추적 및 최적화 목표로 사용할 수 있습니다. GA Conversion과 동일한 개념입니다.

#### 3, FB Pixel Code 구조 이해하기

![FB Pixel code](/img/posts/19/01.png)

만약 우리가 GTM을 활용하지 않는다면 위의 스크린샷처럼 웹 소스코드에 직접 Pixel 코드를 수동으로 삽입해줘야 해요. 마케터인 우리는 코드 삽입은 GTM을 활용하되 이해를 돕기 위해 FB Pixel Code구조를 먼저 살펴볼게요. 

1. Website 오리지널 코드 

   운영하고 있는 웹 사이트의 오리지널 코드입니다. 만약 GTM을 활용하지 않고 직접 코드 수정을 한다면 Facebook pixel 코드는 오리지널 코드 /head 바로 상단에 삽입됩니다. 

2. Facebook pixel 기본코드

   Facebook pixel 기본코드 입니다. 동일한 코드를 삽입하면 되는데 fbq('init', '1234567890') 와 ?id=1234567890의 '1234567890' 부분만 본인의 pixel ID로 교체하면 됩니다. 기본 코드는 '모든 페이지에서 FB Pixel이 작동해'라는 의미에요. 

3. Facebook event 코드 

   /script tag 바로 위에 add to cart 이벤트 코드를 설치한 모습입니다. 
fbq('track', 'Event 명');
   add to cart 자리에 추적하려는 Event 명을 입력하면 됩니다. 

4. Facebook properties코드

   fbq('track', 'Event 명', {properties 이름 : properties 값, properties 2이름 : properties 2 값 });
Event와 함께 변수(FB에서는 Properties로 부름)를 전달하고 싶은 경우 event명 뒤에 {} 에 Key, Value 쌍을 넣어주면 됩니다. Data Layer에서 변수 삽입했던 것과 동일합니다. 

2+3+4번이 이벤트를 추적하기 위한 Pixel 코드입니다. 위의 예시처럼 수동으로 직접 코드를 삽입한다고 하면 이벤트가 발생하는 페이지마다 Pixel코드를 심어줘야 해요. 그런데 마케터가 직접 코드에 손을 대는 것은 어려운 일이죠. 😥 FB에서는 마케터들을 위해서 직접 코드를 수정하지 않고도 event를 전송할 수 있는 기능도 제공하고 있어요! 다음에서 알아볼게요. 

#### 4. FB Event Manager에서 Base Pixel 코드 다운, Event Setup Tool로 이벤트 정의 

GTM으로 추적 Tag를 설치하기 전에 위에서 본 FB Event Manager에서 Base Pixel코드를 다운받고 웹에서 event를 정의해주는 선행 작업을 해줘야 합니다. 여기서 포인트는 FB Event Setup Tool을 활용하면 코드 작성 또는 GTM 이벤트 태그 삽입 없이도 버튼 클릭이나 특정 페이지 url에 대한 이벤트를 바로 추가할 수 있다는 거예요. (아직은 Standard Event만 사용할 수 있데요!) 즉 UI에서 추적하고 싶은 이벤트를 실행시키고 저장하기만 하면 픽셀로 이벤트가 전송된다는 말씀! 간편하죠?

이 내용은 아래 동영상을 보시면서 따라해보세요! 👇👇<br>
[How to Setup Facebook Custom Conversion Events](https://youtu.be/GRJS4eH_diE)

#### 5. GTM FB Pixel Base Tag 추가하기 

GTM에서 FB Tag를 설치하는 과정은 크게 2가지로 나뉩니다. 3-2에서 설명한 페이스북 픽셀 기본 코드를 4번 FB Event Manager에서 다운받아서 GTM에서 기본 태그를 하나 만들고 모든 페이지로 트리거를 걸어두면 기본 픽셀 태그가 이벤트 정보를 받아서 FB Pixel로 보내줘요. GA를 떠올려보면 GA 기본 Tag를 설치한 다음 추적하는 이벤트 별로 GA Tag를 하나씩 설치해줬었잖아요? 동일한 과정이에요. (혹시 기억 안 난다면?! [여기](https://mara.kim/gtm-4-event-utilize/) 클릭) 자세한 설치 방법은 아래 포스팅을 참고해주세요! 👇👇<br>
[GTM으로 FB Pixel설치하기](https://nohze.com/mkt/gtm04_GTM_Facebook/)

#### 6. GTM FB Pixel Evant Tag 추가하기 

Standard event 라면 FB Event Setup Tool을 활용해 이벤트 Pixel로 전송이 가능하지만 Custom event 의 경우에는 GTM을 활용해 추적 Tag를 삽입해서 Pixel로 전송이 필요합니다. 예시로 Add to cart 이벤트에 Product id 변수를 전송하는 Tag를 설치해볼게요. 

**[Add to cart 이벤트 Tag 추가]**

1. 변수 활성화

   우리는 웹에서 발생하는 모든 클릭 중 Add to cart 버튼이 클릭될 때 Tag가 Trigger 되게 만들고 싶기 때문에 Add to cart 버튼 클릭을 구분해 낼 수 있는 변수를 찾아야 합니다. 이 [동영상](https://youtu.be/r87A-Ql2czg)을 참고해주세요!  
   
   - GTM> Variable> Click 관련 기본 제공 변수를 활성화해주고 
   
   - 미리보기 모드를 켠 상태에서 웹 상에서 Add to cart 클릭
   
   - GTM 미리보기> Variables 탭 > Click 관련 변수 값을 확인

2. 트리거 생성 

   - GTM> Trigger> 클릭-모든요소

   - 트리거 조건> 일부 클릭> 필터 조건 입력

     예시) Click classes contains single_add_to_cart_button 

3. 태그 > 맞춤 HTML> FB Add to cart 이벤트 코드 추가 

 [[참고문서] FB Standard event code list](https://www.facebook.com/business/help/402791146561655?id=1205376682832142)

**[Product Id 변수 추가]**

1. GTM 미리보기> Data Layer

   Product Id에 해당하는 데이터 영역 변수 이름을 알아야 하는데요. GTM 미리보기를 통해 Data Layer 탭에서 Product Id 값을 확인할 수 있습니다. 이때 데이터 영역 변수 이름(Key)은 웹 페이지마다 다르고 자신이 운영하는 웹에서 직접 확인해야 합니다. 이 [비디오](https://youtu.be/MPNQmdGZIuQ?t=189)를 참고해주세요. 

2. GTM> 변수> 사용자 정의 변수> 데이터 영역 변수 추가 

   Product Id에 해당하는 데이터 영역변수 이름이 ProductInfo.0.Id 인 경우 변수는 아래와 같습니다. 
   ![GTM Variable](/img/posts/19/02.png)

3. GTM> 태그> 맞춤 HTML> FB add to cart Tag에 변수 추가 

![GTM FB Pixel Tag](/img/posts/19/03.png)

[[참고문서] Required Facebook Pixel Events and Parameters for Daynamic Ads](https://www.facebook.com/business/help/606577526529702)

#### 7. FB Event Manager에서 Custom Conversion 지정

Event를 셋팅하면 Custom event를 Conversion으로 지정해서 tracking 과 광고 최적화를 할 수 있습니다. custom event 를 custom conversion과 mapping을 시켜야지만 광고 추적과 최적화가 가능합니다. 

![FB Custom Conversion](/img/posts/19/04.png)


이렇게 custom converison을 만들면 캠페인 목표를 전환으로 설정했을 때 conversion으로 ScrollTracking_75% 를 사용할 수 있습니다. 

[[참고문서] Facebook Custom Conversion](https://www.jonloomer.com/facebook-custom-conversions/)

[번외]앱 이벤트 셋팅 

비교적 간단한(?) 웹과 달리 앱은 개발자의 도움이 필요합니다. 우선 웹에서 Pixel역할을 하는 FB SDK를 설치 후 개발자의 도움을 받아 코드로 event를 셋팅해줘야 해요. 이 내용은 기회되면 따로 포스팅 해볼게요. <br>오늘도 칼퇴하세요 ~!  🙋‍♀️