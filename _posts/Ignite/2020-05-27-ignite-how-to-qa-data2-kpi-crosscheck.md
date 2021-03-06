---
layout: post
permalink: /ignite-how-to-qa-data2-kpi-crosscheck/
title: '[일잘러스킬]데이터검증허니팁2-KPI로 크로스체크하기'
date: 2020-05-27 12:00:00 +09:00
feature: '/img/ignite/04/01_T.png'
background: '/img/ignite/04/01_B.png'
categories:
  - ignite
tags:
  - 엑셀
  - 데이터분석
  - 데이터 추출
  - 퍼포먼스 마케팅 
  - 더블체크
  - 크로스체크
  - 크로스체크 더블체크
  - 데이터분석
  - KPI설정
description: 'KPI 레퍼런스삼아 데이터 검증하기'
content_id: '4'
---

안녕하세요~!<br>
프로이직러 Mara입니다.

[이전 글](https://mara.kim/ignite-how-to-qa-data1/)에서는 데이터를 크로스 체크 해야 하는 이유, 그리고 상식에 근거해서 크로스 체크할 수 있는 방법까지 알아봤는데요. 크로스 체크를 하지 않고 틀린 데이터를 전달하게 되면 일도 2번 하게 되고,  업무 기회도 잃고, 신뢰도 잃을 수 있으니 꼭꼭 크로스체크하셔서 캍퇴하시기 바랍니다. 이번글에서는 KPI로 크로스 체크할 수 있는 꿀팁을 소개할게요. 

우선 KPI라는 용어가 무엇인지부터 살펴볼까요? 다들 잘 아시겠지만, KPI(Key Performance Index) 란 회사의 핵심 목표를 수치화할 수 있는 지표로 환산해서 목표 달성 여부를 측정하는 지표인데요. 모든 회사는 각 비즈니스의 현재 상태를 반영할 수 있는 KPI를 가지고 있습니다. 좋은 KPI는 다음과 같은 특징을 가지고 있습니다. 

1. 측정 가능하다
2. 변화하는 비즈니스 상황을 반영한다
3. 비교 가능하다
4. 목표 달성 기한이 있다

예를 들어 볼게요. '회사 매출액을 성장시킨다.'라는 KPI는 위에서 말한 좋은 KPI의 특징에 부합하지 않습니다. 일단 이 KPI는 측정 가능하지 않습니다. 성장을 시킨다고 하면 얼마나 성장을 시켜야 목표를 달성한다고 할 수 있을까요? '얼마나' 성장해야 성장이라고 정의할 수 있는지 측정 가능한 기준을 제시해주는 게 좋습니다. 그럼 '회사 매출액이 1억이 늘어난다'라고 하면 성장이라고 할 수 있을까요? 1억이란 절대액은 비즈니스에 따라서 또 회사에 따라서 많은 금액일 수도 적은 금액일 수 있습니다. 회사 전체 매출액이 10억이었을 때랑 100억이었을 때 1억은 굉장히 다른 의미이겠죠? 그럼 이렇게 변화하는 비즈니스 상황을 반영하기 위해서는 어떻게 KPI를 잡으면 좋을까요? '비율'로 표현해서 변화하는 비즈니스 상황을 반영하면 됩니다. '회사 매출액이 10% 성장한다'라고 하면 어떨까요? 어떤 숫자를 기준으로 10% 성장인지가 명확하지 않습니다. 작년 매출액 대비, 이번 연도 1분기 대비와 같이 비교할 수 있는 기준이 필요합니다. 마지막으로 '회사 작년 매출액 대비 10% 성장한다'라고 하면 어떨까요? 언제까지 10% 성장하는 경우 KPI달성인지가 명확하지 않습니다. 어떤 목표를 1년 동안 달성하는 것과 1분기 안에 달성하는 것은 완전히 다른 action plan 이 나올 테니까요. 

### 데이터 검증 🍯Tip2. KPI로 크로스체크하기

이렇게 KPI를 정하게 되면 회사 KPI를 정기적으로 모니터링하게 됩니다. KPI를 일의 자리 수 까지 외우고 있을 수는 없지만 대략적으로라도 평균 KPI수치를 머릿속에 가지고 있을 필요가 있습니다. 예를 들어 우리 부서의 KPI가 CTR(Click through rate)이라고 할 경우 '배너 광고의 CTR은 평균적으로 0.7%야'라는 데이터를 머릿속에 가지고 있으면 CTR 5%라는 데이터를 마주했을 때 원인을 파악해봐야겠다는 생각이 들 겁니다.

평균 KPI를 모른다면 해당 데이터가 잘 나온 데이터 인지, 못 나온 데이터 인지 해석하기도 어렵고 이 데이터를 가지고 해야 할 넥스트 스텝도 명확하지 않으니까요. 회사마다 중요하게 생각하는 KPI가 다르고 모니터링하는 주기도 일, 주, 월, 분기 등 다릅니다. 본인이 일하고 있는 회사의 적어도 최근 3개월 데이터 정도는 꼼꼼히 뜯어보면서 전체 성과의 추세가 상승인지 하강인지, 각 KPI의 평균 적인 수치는 어느 정도이고 성과에 어떤 식으로 기여하고 있는지 과거 데이터를 보면서 기본적인 회사의 수익구조를 이해하고 있어야 합니다.

그렇다면 레퍼런스 삼을 만한 데이터가 없을 땐 어떻게 해야 할까요? 예를 들어 처음으로 시도한 A/B 테스트의 성과를 해석해야 하는데, 이전에 시도해 본 적이 없기 때문에 이 결과 자체가 의미 있는 데이터 인지, 확장시켜서 적용해도 되는 것인지 판단하기 어려울 수 있는 거죠. 이럴 때는 비슷한 동종업계의 데이터를 참고하거나 회사 내의 이전 데이터를 레퍼런스 삼아서 성과를 평가하면 됩니다. 

이번 글에서는 KPI를 기준으로 데이터를 크로스 체크하는 방법에 대해서 알아봤습니다. 다음 글에서는 데이터 검증 🍯Tip 시리즈 마지막 편인 피봇테이블로 데이터 검증하는 방법에 대해서 글을 작성해볼게요. <br>
오늘도 칼퇴하세요~! 🙋‍♀️  