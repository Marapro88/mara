---
layout: post
permalink: /gtm-3-preview-debugging/
title: '[디지털마케팅]마케터의 GTM활용 가이드_3편'
date: 2021-01-16 12:00:00 +09:00
feature: '/img/posts/17/01_T.jpg'
background: '/img/posts/17/01_B.jpg'
categories:
  - marketing
tags:
  - 스타트업
  - 디지털마케팅
  - 마케팅
  - GTM
  - 미리보기
  - 디버그
  - 일잘러
  - 프로이직러
  - 프로이직러 Mara
description: 'GTM 미리보기로 디버깅하기'
content_id: '1016'
---

안녕하세요~!<br>
프로이직러 Mara입니다.

이전 포스팅에서 GTM의 정의, 기본적인 지식과 DataLayer 개념까지 알아보았는데요. <br>
복습이 필요하다면 아래 포스팅을 참고해주세요. 

[마케터의 GTM활용 가이드_1편 GTM 활용에 필요한 기초지식](https://mara.kim/gtm-0-basic-knowledge/)

[마케터의 GTM활용 가이드_2편 DataLayer이해하기](https://mara.kim/gtm-1-data-layer/)

GTM으로 Tag를 셋팅했다면 GTM의 미리보기로 디버깅을 할 차례입니다. 개발자들은 열심히 개발해서 배포했는데 이슈가 발생하면 '버그가 생겼다'라고 표현하는데요. GTM 미리보기를 사용하면 GTM에서 만든 Tag가 정상 작동하는지 미리 보고 버그를 디버깅할 수 있습니다. 앱의 Test 서버 같은 역할을 한다고 이해하시면 돼요! 

#### 1. GTM 미리보기 구조 이해하기 

GTM Debug mode(또는 GTM Console)을 실행하면 크게 5가지 정보를 제공합니다. 

![GTM Layout](/img/posts/17/01.JPG)

1. Event Timeline 
실행되는 모든 이벤트를 확인할 수 있습니다. 하나의 아이템 = 하나의 이벤트라고 생각하면 됩니다. 
   
2. Tags 
실행된 Tag와 Tag 정보를 확인할 수 있습니다. 
   
3. Variables
Variable 정보를 확인 할 수 있습니다. variable name & type, return type, value를 확인할 수 있습니다. 
   
4. Data Layer 
웹 소스코드에서 push 한 Data Layer정보를 확인 할 수 있습니다. 실제로 data layer가 어떻게 날아오는지 확인할 수 있습니다. 여기서 확인한 정보는 모두 변수로 활용 가능합니다.
   
5. Errors 
에러가 있으면 표시합니다. tab에 숫자가 없다면 에러도 없다는 뜻입니다. 

#### 2. GTM 미리보기 Built-in Event

GTM 미리보기를 조금만 써보면 아시겠지만 항상 Container Loaded / DOM Ready/ Window Loaded 3가지 event 가 자동으로 나타납니다. 왜 때문일까요? 😶<br>
이 내용은 GTM > Trigger> 트리거 유형> 페이지뷰 와 관련 있어요!

![GTM Trigger Page View](/img/posts/17/02.JPG)

브라우저에서 조회하는 웹 페이지는 한 번에 다 로드되는 것 같지만 사실은 3번에 걸쳐서 로드되고 있어요. 다만 그 간격이 너무 짧아서 한꺼번에 로드되는 것 처럼 보입니다. 순차적으로 가장 먼저 Container, 그 다음 DOM, 마지막으로 Window가 로드됩니다. 각 페이지 뷰마다 사용할 수 있는 변수가 조금씩 달라지기 때문에 원하는 정보가 어느 페이지 뷰에서 로드 되는 지를 파악하고 트리거를 만들어야 합니다. 

1. Container Loaded 

   - Head에 심은 GTM 스크립트가 실행되는 시점 

   - 아직 전체 페이지가 로드되지는 않아서 유저는 웹페이지에서 조회할 수 있는 내용이 없는 상태 
   - 가장 빠르게 GTM 태그를 실행해야 할 때 사용

2. DOM Ready 

   - HTML 태그가 실행되는 시점 

   - 유저가 웹페이지 일부 구성요소를 조회할 수 있음 

3. Window Loaded

   - 자바스크립트 요소까지 모든 웹페이지가 로딩된 순간 

와 닿지 않으시는 분들을 위해 이벤트 list에서 Container Loaded와 DOM Ready Variables 탭을 비교해볼게요. Container Loaded 이벤트는 몇몇 데이터 영역 변수가 undefined로 확인되지 않는 반면 DOM Ready 이벤트는 variable value가 모두 채워진 것을 확인할 수 있습니다.

![GTM Container Load](/img/posts/17/03.JPG)

![GTM DOM](/img/posts/17/04.JPG)

Container Loaded는 아직 전체 페이지가 로드되지 않은 시점이기 때문에 웹페이지 구성 요소 (제목, 콘텐츠 id 등) 정보를 알 수가 없어서 변수를 채우지 못하는 거에요. HTML 태그가 로드되는 DOM 시점에는 page.title이나 page.content_id를 불러오기 때문에 변수가 채워져 있습니다. 따라서 page.title을 변수로 사용하고 싶다면 Container Loaded(GTM Trigger에서는 페이지뷰)가 아닌 DOM Ready를 trigger로 선택해주셔야 해요. 

#### 3. GTM 미리보기로 Tag 디버깅하기 

미리보기가 웹에 연결된 상태에서 Tag에서 정의한 이벤트를 발생시켰을 때 Tag가 정상 작동해서 Event와 Variable이 전달되는지 확인할 수 있어요. 예시로 2분 이상 글을 읽었을 때 Timer 이벤트가 날아오도록 셋팅한 Tag를 가지고 어떻게 디버깅하는지 볼게요. 

1. GTM > Tag에서 만든 Tag 중 실행된 태그와 실행되지 않은 태그를 확인할 수 있습니다. 만약 새로운 태그를 만들고 글을 2분 이상 읽었는데도, Event timeline에 'Spent_2min'가 나타나지 않는다면 Tag에 오류가 있는 거예요. 다행히 2분이 지나니 Tag 이벤트명에 입력한 이벤트가 짠! 하고 나타납니다. 어떻게 연결되는지 그림이 그려지시나요? 

   

   ![GTM Tag-Event name](/img/posts/17/05.JPG)

   ![GTM Tag-Event name](/img/posts/17/06.JPG)

   

2. Variables

   GTM > Variable에서 만든 Variable 이 정상적으로 이벤트와 함께 전송되고 있는지 확인할 수 있습니다. GTM 셋팅 화면과 미리보기 모드는 이렇게 연결됩니다. 

   

   ![GTM Variable-User defined variable](/img/posts/17/07.JPG)

   ![GTM Preview-Variable](/img/posts/17/08.JPG)

   

3. Data Layer

   웹 소스코드에 Data Layer를 추가한 뒤 GTM에서 사용자 정의 변수를 생성, 이를 활용해 Trigger를 만들었다면 Data Layer 탭에서 사용자 정의 변수가 정상적으로 셋팅되었는지 확인할 수 있어요. 

   ![GTM Preview-DataLayer](/img/posts/17/09.JPG)

이번 포스팅은 GTM 미리보기 활용법에 대해 알아보았습니다.<br>오늘도 칼퇴하세요 ~!  🙋‍♀️

[[참고문서]GTM 미리보기](https://support.google.com/tagmanager/answer/6107056?hl=ko)

[[참고문서]A Guide To Google Tag Manager Preview Mode](https://www.analyticsmania.com/post/google-tag-manager-debug-mode/#timeline)