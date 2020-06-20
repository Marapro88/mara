---
layout: post
permalink: /marketing-braze-honey-tip3-report-data-analytics/
title: 'Braze 마케팅 꿀팁 3_리포트 성과측정'
date: 2020-04-05 12:00:00 +09:00
feature: '/img/posts/04/02_Thumnail.jpg'
background: '/img/posts/04/01_Back.jpg'
categories:
  - marketing
tags:
  - 스타트업
  - 밸런스히어로
  - 마케팅
  - 핀테크
  - Braze 마케팅
  - 메시지마케팅자동화
description: 'Braze Push/In-app message메시지 데이터 해석 및 Report 설정 방법'
---

안녕하세요~!<br>
프로이직러 Mara입니다. 

이전 글에서는 우리 고객인 Target user에게 개인화된 마케팅 메시지를 전달하기 위해 캠페인을 생성해봤습니다. 그럼 메시지의 성과가 좋았는지 나빴는지 측정해봐야겠죠?
오늘은 성과측정을 위한 Report 설정 방법과 데이터 해석에 대해서 알아보겠습니다.

![이미지1](/img/posts/04/01.png)

Campaigns에서 성과측정을 원하는 캠페인을 클릭합니다.

![이미지2](/img/posts/04/02.png)

클릭하고 들어가면 제일 먼저 이런 화면을 만나게 됩니다. 하나씩 살펴볼게요.
### 1.Report 기간 설정
Report 기간은 default로 처음 발송일부터 오늘까지로 설정되어 있습니다. 기간을 바꾸고 싶으면 드롭다운 목록을 누르고 원하는 기간을 선택하면 됩니다. Custom range를 선택하면 직접 기간을 설정할 수 있습니다.
![이미지3](/img/posts/04/03.png)

### 2. User Data

내부 DB와 엮어서 데이터를 분석하려고 할 때 메시지 발송 대상 리스트가 필요합니다. 그 경우에는 CSV Export All Recipient Data를 선택하면 메시지 발송 대상자를 CSV 파일로 다운로드할 수 있습니다. 다만 500k 이상의 유저에게 발송된 경우에는 제공하지 않습니다.

![이미지4](/img/posts/04/04.png)

### 3.Campaign Details

캠페인 전체의 기본적인 성과를 확인할 수 있는 영역입니다.

<ol>Messages Sent: 조회 기간 동안의 메시지 총 sent 개수</ol>

<ol>Total Open Rate: (Direct opens+Influenced opens)/Messages Sent</ol>

<ol>Direct opens: 해당 푸시를 통해 직접 열린 푸시 알림의 총수</ol>

<ol>Influenced opens: 푸시 알림을 전송한 후 푸시를 직접 열지 않고 앱을 연 총 사용자 수</ol>

<ol>Conversion rate: 전송된 메시지의 모든 수신자와 비교하여 정의된 이벤트가 발생한 비율. Conversion setting에서Event A(Primary)에 설정된 값을 사용.</ol>

<ol>Estimated Audience: Push 메시지를 받은 사용자 수. Braze추정 값.</ol>

<h3>4.Setting(Delivery/Audience/Conversion)</h3>

캠페인 생성 시 세팅 조건을 확인할 수 있는 영역입니다.

![이미지4-1](/img/posts/04/0401.png)

### Android Push Performance

1개의 캠페인에 여러 가지 메시지를 전달한 경우 각 메시지 별로 성과를 비교해볼 수 있는 영역입니다. 동일한 유저 대상으로 어떤 메시지 또는 creative가 가장 효과적이었는지 측정할 때 유용하게 쓰일 수 있습니다.

```
Bounce rate: 실패한 총 메시지 수입니다. 유효한 푸시 토큰이 없거나 이메일 주소가 잘못되었거나 비활성화되었거나 캠페인이 시작된 후 사용자가 구독을 취소했기 때문에 이러한 문제가 발생할 수 있습니다.
```

[Repoort Metrics Glorssary바로가기](https://www.braze.com/docs/user_guide/data_and_analytics/report_metrics/)

Braze에서는 친절하게 지표 용어집을 제공하고 있습니다. 필요한 측정 항목을 검색하거나 채널별로 필터링해서 사용해보세요.

## 데이터 해석

Braze 메시지 성과를 분석할 때는 Primary conversions를 sent, open, direct oepn 수치들을 참고하면서 효과를 측정합니다. 지표를 먼저 확인하고 가장 우수한 퍼포먼스를 보인 메시지는 무엇이었고 왜 이 메시지가 좋을 성과를 냈는지 발송 단계에서 세웠던 가설들을 검증해보는 거죠. 이런 식으로 몇 번의 A/B Test를 거치면 메시지 calibration목적으로 사용할 수 있습니다.  

## 🍯Tip 1. 여러 가지 캠페인 한번에 모아서 리포트 보기

캠페인을 진행하다 보면 여러가지 캠페인을 한꺼번에 성과를 비교해가면서 보고 싶을 때가 있습니다. 그럴 때는 왼쪽 Navigation bar> DATA> Engagement Reports> +Create New Report를 눌러줍니다.

![이미지5](/img/posts/04/05.png)

누르고 들어가면 아래와 같은 화면을 만나게 될 거예요..

![이미지6](/img/posts/04/06.png)

1.Manually select Campaigns and Canvases
디폴트 설정 값입니다. 직접 보고 싶은 캠페인을 고를 수 있다는 의미이니 그대도 사용하시면 됩니다.

2.검색하고자 하는 키워드를 입력해서 성과를 측정하고 싶은 캠페인을 찾습니다.

3.”Last Edited”를 마우스 오버해서 3번 눌러주면 최근 순으로 캠페인을 정렬할 수 있습니다.

4.리포트에“+ADD”버튼을 눌러줍니다.

여기까지 제대로 따라오셨다면 이런 화면을 만나실 수 있으실 거예요..

![이미지7](/img/posts/04/07.png)

아래로 내려가서 ‘Add stats’ 버튼을 stage로 넘어갑니다.
여기서 보고 싶은 측정 지표들을 선택할 수 있습니다.

![이미지8](/img/posts/04/08.png)

리포트 발송과 관련된 정보를 입력합니다.

1. 리포트 제목, 압축 여부, 전달받을 메일 주소를 입력합니다.

2. 데이터 기간을 설정합니다.

3. 데이터 Display 기간을 설정합니다. 예를 들어 일단위로 데이터를 볼 것인지 주 단위로 볼 것인지를 여기서 설정할 수 있습니다.

4. 리포트 발송 스케줄을 설정할 수 있습니다.

5. Confirm 버튼을 눌러주면 발행 완료.

Braze 잘 활용하셔서 유저에게 시의적절한 마케팅 메시지 전달하시기 바랍니다.

오늘도 칼퇴하세요 ~! 🙋‍♀️