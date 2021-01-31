---
layout: post
permalink: /gtm-2-data-layer/
title: '[디지털마케팅]마케터의 GTM활용 가이드_2편'
date: 2021-01-09 12:00:00 +09:00
feature: '/img/posts/16/01_T.jpg'
background: '/img/posts/16/01_B.jpg'
categories:
  - marketing
tags:
  - 스타트업
  - 디지털마케팅
  - 마케팅
  - GTM
  - 데이터영역
  - 데이터 영역변수
  - Data Layer
  - Trigger에서 사용자정의변수 활용
  - Trigger에서 데이터영역 이벤트 활용
  - 사용자 정의 변수
  - 일잘러
  - 프로이직러
  - 프로이직러 Mara
description: 'Data Layer 이해하기'
content_id: '1015'
---

안녕하세요~!<br>
프로이직러 Mara입니다.

지난 포스팅에서 GTM 기초지식에 대해 살펴보았습니다. 이번 포스팅에서는 GTM을 100% 활용하기 위해 꼭 알아야 하는 개념인 'Data Layer'에 대해 알아보겠습니다. GTM 이 무엇인지부터 알고 싶다면 [여기](https://mara.kim/gtm-0-basic-knowledge/)를 클릭해주세요.

#### 1. Data Layer(데이터 영역)정의

구글 개발자 문서에서는 데이터 영역을 아래와 같이 정의하고 있는데요.

> 데이터 영역이란 웹사이트에서 태그 관리자 컨테이너로 정보를 전달할 때 사용되는 자바스크립트 개체를 말합니다. 이렇게 전달된 정보는 태그 구성 시 변수를 게재하거나 트리거를 활성화하는 데 사용됩니다. 태그 관리자는 변수, 거래 정보, 페이지 카테고리 및 페이지 곳곳에 존재하는 기타 중요 신호를 참조하는 대신 데이터 영역 소스 코드에 있는 정보를 쉽게 참조하도록 설계되었습니다. 데이터 영역은 변수를 비롯한 연결된 값을 사용해 구현되기 때문에 태그를 실행해야 할 때 변수와 값을 바로 사용할 수 있습니다.
>

데이터 영역 이란 동적으로 값을 할당할 수 있는 변수를 간단한 코드로 사용자가 선언해주면 GTM에서 이를 감지하고 맞춤 이벤트, 사용자 정의 변수로 활용 가능한 기능입니다. 웹에서 아래 코드를 통해 Data Layer를 쓸 수 있어요.

![dataLayer코드형식](/img/posts/17/07.JPG)

코드를 이해하려면 약간의 자바스크립트 지식이 필요한데요. 한번 찬찬히 봐볼게요. Data Layer는 Key/value 쌍으로 구성되어 있습니다. dataLayer = [{ }]; 안에 `:` 앞에 오는 값이 key가 되고 `:` 뒤에 오는 값이 value가 됩니다. Key는 공통적으로 활용할 수 있는 매개변수의 이름이 되고 Value는 변하는 동적값이나 고정값을 할당할 수 있는 매개변수의 값이 됩니다.(변수명을 {{' '}}로 감싸주면 동적 값이 됩니다🙂) 위의 코드를 응용해서 유저가 페이지 조회를 했을 때 맞춤 이벤트와 2가지 매개 변수를 전달하는 데이터 영역 변수를 작성하면 아래와 같습니다.

```
<script>
dataLayer = [{
    'event': 'ViewContent',
    'content_name': '{{page.title}}',
    'content_id': '{{page.content_id}}'
  }];
</script>
```



- 맞춤 이벤트 이름: ViewContent
- 데이터 영역 변수 이름 : content_name, content_id
- 사용자 정의 변수 : page.title, page.content_id

이 코드를 보면서 실제로 GTM 인터페이스에서 input값이 어떻게 구성 되는 지 살펴볼게요.

[[참고문서] Using Data Layer-Google Developer Guide](https://developers.google.com/tag	-manager/devguide#datalayer)

#### 2. Variable에서 Data Layer 활용법

웹 소스코드에서 위와 같이 Data Layer를 선언해준 뒤 GTM 변수에서 데이터 영역 변수를 셋팅하면 됩니다. **Data Layer 만 추가하고 GTM에서 변수 추가하여 Tag를 만들어서 보내주지 않으면 GA나 FB에서 확인할 수 없습니다!** 페이지 제목에 대한 데이터 영역변수를 셋팅하는 방법은 다음과 같습니다.

1. GTM> 변수 > 사용자 정의 변수 선택
2. 사용자 정의 변수 이름에 Value에 해당하는 `page.title` 입력
3. 변수 구성> 데이터 영역 변수 선택
4. 데이터 영역 변수 이름에 key 에 해당하는 `content_name` 입력
5. 저장

![사용자정의변수](/img/posts/16/01.JPG)

#### 3. Trigger에서 Data Layer 활용법

이렇게 생성한 변수는 Trigger에서 event 실행 조건 필터를 설정할 때 활용할 수 있습니다. 페이지 제목에  `essay`를 포함하는 경우 작동하는 Trigger를 만들면 다음과 같습니다.

1. 트리거> 새로 만들기
2. 트리거유형 '페이지뷰-DOM사용 가능' 선택
3. 이 트리거는 다음에서 실행됩니다> '일부 DOM사용 가능 이벤트' 선택
4. 변수 목록에서 'page.title'선택
5. 원하는 조건 지정 후 저장

![Trigger-사용자정의변수](/img/posts/16/02.JPG)

#### 4. Trigger에서 맞춤 이벤트  활용법

웹 소스코드상에서 Data Layer를 통해 선언해준 event를 활용하여 GTM 트리거에서 맞춤 이벤트 트리거를 셋팅하는 방법입니다. 이벤트 이름에 Data Layer에서 선언해준 event 명과 동일한 단어를 적어줘야 GTM에서 이벤트를 감지할 수 있어요!

1. 트리거> 새로 만들기> 트리거 구성 선택
2. 트리거 유형> 맞춤 이벤트 선택
3. 이벤트 이름에 ViewContent 입력
4. 트리거 실행 조건 필요에 따라 선택 후 저장

![Trigger-사용자정의변수](/img/posts/16/03.JPG)

**맞춤 이벤트로 Trigger를 만든 후(언제 보낼지) Tag를 통해서 어디로 어떤 이벤트를 보낼지 까지 지정 해줘야 합니다.**  예시로 GA4로 Event를 전송하는 Tag를 구성해보겠습니다. 당연히 다른 Tag 유형을 통해 FB이나 다른 광고 플랫폼으로도 전송할 수 있습니다.

1. 태그 > 새로 만들기 선택
2. 태그 이름 설정
3. 태그 구성 선택
4. 태그 유형 > Google 애널리틱스 : GA 이벤트 선택
5. 구성태그 > GA4 Config Tag 선택
6. 이벤트 이름 > GA에서 사용할 이벤트 이름 입력
7. 이벤트 매개변수 > 행 추가 선택> 사용자 지정 변수 Key/Value 입력
8. 트리거> 트리거 선택> 'ViewContent' 선택
9. 저장

![Tag-trigger 맞춤이벤트](/img/posts/16/04.JPG)

여기까지 완료 후 제출하면 GA 상에서 ViewContent 이벤트를 페이지 제목 매개변수와 함께 확할 수 있습니다.

[[참고문서] Custom event trigger-Tag Manager Help](https://support.google.com/tagmanager/answer/7679219?hl=en&ref_topic=7679108)

#### 5. Tag에서 Data Layer 활용법

위의 예시처럼 사용자 지정 변수를 셋팅해두면 Tag에서 이벤트 매개변수로 활용 가능합니다. 특히 커머스 전환 구매가를 동적으로 추적할 때 유용하게 사용되더라구요. 구글링 해보면 자료는 많으니 관심 있으신 분들은 'how to track conversion values with GTM'으로 검색해보세요!

#### 6. Variable vs Data Layer

그럼 Variable을 활용하는 것과 데이터 영역 변수를 활용하는 것은 어떤 차이점이 있을까요? 예를 들어 기본 제공 변수에 Page Path는 굳이 Data Layer로 선언해주지 않아도 GTM에서 활용이 가능하거든요. 사실 이 부분은 저도 아직 명확히 이해를 못했지만, 이해한 내용을 적어보자면 Variable은 해당 변수가 페이지에서 로드가 되는 시점까지 기다려야 하지만 Data Layer는 특정 event가 trigger 되는 순간 variable이 함께 날아오기 때문에 tag가 작동하자마자 variable이 즉시 사용 가능하다. 정도로 이해했어요.  

이번 포스팅은 GTM 활용을 위해 꼭 알아야 하는 Data Layer에 대해서 알아보았습니다.<br>오늘도 칼퇴하세요 ~!  🙋‍♀️
