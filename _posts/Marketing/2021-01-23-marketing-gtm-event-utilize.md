---
layout: post
permalink: /gtm-3-event-utilize/
title: '[디지털마케팅]마케터의 GTM활용 가이드_4편'
date: 2021-01-23 12:00:00 +09:00
feature: '/img/posts/18/01_T.jpg'
background: '/img/posts/18/01_B.jpg'
categories:
  - marketing
tags:
  - 스타트업
  - 디지털마케팅
  - 마케팅
  - GTM
  - GTM event 추가
  - GTM variable 추가
  - GTM 이벤트 추가  
  - GTM 맞춤변수 추가    
  - 일잘러
  - 프로이직러
  - 프로이직러 Mara
description: 'GTM-GA 이벤트&변수 연동'
content_id: '1017'
---

안녕하세요~!<br>
프로이직러 Mara입니다.
이번 포스팅에서는 GTM에서 GA로 전송한 데이터를 활용하는 방법에 대해 알아보겠습니다.

#### 1. GA4 All Event

GTM에서 Tag를 통해 event를 전송하면 `GA4 > Events> All Events`에 **자동으로 연동**됩니다. (편리하죠?😀) 실시간은 아니고 24시간 후에 들어옵니다. Event와 관련된 configuration 기능을 하는 공간이 All event입니다. 여기서 제공하는 기능은 크게 3가지입니다.

- Modify an event

  이 기능은 주로 만들어진 이벤트에 대한 오타 수정, 매개변수 추가, 실제로는 동일한 이벤트지만 이벤트명이 다른 이벤트 Merge 같은 이벤트 수정 작업을 GTM을 거치지 않고 바로 할 수 있습니다. 조건을 걸어서 이벤트를 세분화시킬 수도 있습니다. 예를 들어 $100 이상 구매 건을 별도 이벤트로 구분해서 보고 싶은 경우 아래와 같이 세팅할 수 있습니다.

  ![GA Modify an event](/img/posts/18/01.jpg)

- Create a event
  기존 이벤트와 변수를 결합해서 새로운 이벤트를 만들 수 있습니다. 예를 들어 ViewContent 이벤트 중 contact페이지를 조회한 이벤트만 확인하고 싶은 경우(url 이 mara.kim/contact라고 가정) 매칭 컨디션과 맞춤 이벤트 이름에 GA4에서 조회하고 싶은 이벤트 이름을 부여하면 됩니다.
  ![GA Create event](/img/posts/18/02.jpg)

위에서 언급한 이벤트 수정, 추가 기능은 Web만 지원됩니다.😥 앱 이벤트에 대해서는 개발자를 통해 Firebase에 이벤트를 심어주는 과정이 필요합니다. (이 내용은 Firebase 활용법에서 별도로 연재할 예정이니 기대해주세요!😝)

![GA App은 안돼요](/img/posts/18/03.jpg)

- Manage Custom Definition
  자동으로 GA4에서 확인 가능한 event와 달리 Variable(이벤트 매개변수)은 Built-in 이건 custom 이건 **별도로 GA인터페이스상에서 등록이 필요**합니다. `GA4> Events> All events> Manage Custom Definitions`에서 등록할 수 있습니다. `GTM> Variable> 데이터 영역 변수`에서 데이터 영역 변수 이름을 확인하고 `GA4> Events> All events> Manage Custom Definitions> Event parameter name`에 데이터 영역 변수를 등록해주세요. <br>
  하나 주의해야 할 점은 Variable명도 대소문자를 구분하기 때문에 tag에 추가한 variable 명과 동일하게 등록을 해주어야 합니다. content_name을 Content_name로 등록하면 GA4는 다르게 인식해서 GA4에서 변수를 확인할 수 없습니다. 등록 후 24시간 정도 후 확인 할 수 있습니다.

![GTM 변수 구성화면](/img/posts/18/04.jpg)

![GA 변수 등록](/img/posts/18/05.jpg)

- Report

이렇게 등록해준 Event/Variable은 GA4 2가지 리포트에서 확인 가능합니다.  

1. GA4> Engagement> Events > Event name ➕버튼 클릭> 맞춤(이벤트 범위)

   측정기준에서 등록한 이벤트 매개변수를 확인 할 수 있습니다.

![GA 이벤트 확인](/img/posts/18/07.jpg)

2. Analysis> Analysis Hub reports> 측정기준 ➕버튼 클릭> 맞춤 측정기준
   variable이 정상적으로 등록되었다면 맞춤 측정기준에서 등록한 variable을 찾을 수 있습니다. 등록 후 24시간이 지나면 확인 가능합니다.

[[참고문서]Modify and create events](https://support.google.com/analytics/answer/10085872)

[[참고문서]A Guide to custom dimensions in GA4](https://www.analyticsmania.com/post/a-guide-to-custom-dimensions-in-google-analytics-4/)

#### 2. GA4 Conversion

- Conversion 이란?
  각 서비스에게 수익을 안겨주는 유저 행동을 디지털 마케팅에서 Conversion(전환)이라고 지칭하는데요. 전환을 일으키는 오디언스를 구분해낼 수 있으면 구매를 일으킬 가능성이 높은 유저의 특성이 무엇이고 서비스에서 어떤 행동을 하는지 추적이 가능해집니다. 마케팅 전략을 세우는 데 도움이 되겠죠?

- Custom conversion
  GA4에서 Predefined Conversion을 제공하지만 대부분 custom conversion을 사용해야 하는데요. Event > All event에서 conversion으로 지정하고 싶은 이벤트 오른쪽의 토글바를 활성화시키는 방식으로 간편하게 지정할 수 있습니다.

- Conversion 조회
  `Acquisition > Traffic Acquisition` 페이지 별 전환 count를 조회할 수 있습니다.

![GA 전환](/img/posts/18/06.jpg)

#### 3. Analytics에서 Custom Segment 추가하기

User의 특징, 속성에 따른 성과의 차이를 관찰하고 싶을 때 Custom segments를 활용할 수 있습니다. 특정 segment에 속한 유저가 높은 리텐션을 보인다면 해당 유저를 어떻게 우리 앱에 더 끌어 모을 수 있을까를 고민해볼 수 있겠죠?

- 새 잠재고객 만들기

GTM으로 만든 이벤트와 변수를 활용하여 유저 세그먼트를 만들고 이것을 구글 애즈와 연동하여 리마케팅 모수로 활용할 수 있습니다.

1. 새 잠재고객을 클릭

2. 맞춤 잠재고객 만들기 클릭

3. 잠재고객 이름과 설명 입력

4. 이벤트(Events) 선택

5. 조건 범위(condition scope)

6. - 모든 세션: 사용자가 상호작용하는 전체 기간 동안 모든 조건이 충족되어야 합니다.

   - 동일한 세션 내: 동일한 세션에서 모든 조건이 충족되어야 합니다.

   - 동일한 이벤트 내: 단일 이벤트에서 모든 조건이 충족되어야 합니다.

   - - 세션은 유저가 서비스에 접속한 시점부터 사용자 측에서 활동이 멈춘 후 30 분 뒤 종료
     - 모든 세션 < 동일한 세션< 동일한 이벤트 순으로 상위 개념.

7. 시퀀스 추가

8. - 특정 순서로 진행되는 조건을 충족하는 사용자를 추가할 수 있고, 원하는 경우 특정 기간을 설정할 수 있습니다. 예 : 1단계: first_open, 2단계: in_app_purchase

9. 특정 사용자를 제외하는 조건을 만들려면 제외할 그룹 추가를 클릭합니다

10. - 제외 조건을 활용해 퍼널 전 단계 완료 & 이후 단계 미완료 세그먼트를 만들고 리타겟팅 할 수 있습니다.

11. 포함 기간: 사용자를 잠재고객으로 유지하는 기간을 입력(1~540일)

12. 저장

🍯Tip) Suggested segments를 보면 구글에서 자주 사용하는 세그먼트를 미리 제공하고 있습니다. 참고해서 세그먼트를 만들어보세요.

Segment를 잘 활용하려면 퍼널 이벤트, 전환 이벤트, 전환 value 데이터가 충분히 있어야 하는데 GA4는 아직 demo account를 제공하지 않더라구요. GA4 demo account 가 나오는 데로 분석파트는 적절한 예시와 함께 업데이트 할게요! 이번 포스팅은 GTM과 GA를 연동해서 Event와 Variable 활용법에 대해 알아보았습니다.<br>오늘도 칼퇴하세요 ~!  🙋‍♀️

[[참고동영상]구글 애널리틱스 세그먼트 이해하기](https://www.youtube.com/watch?v=8SmD3y4FKBM)
