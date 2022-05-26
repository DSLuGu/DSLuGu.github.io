---
layout: post
title: 시계열 데이터 분석
subtitle: 시계열 데이터 이론 및 방법론
date: 2022-05-26
categories: Statistics
tags: [time-series, ]
---


이번 글은 시계열 데이터에 대한 내용 정리를 목적으로 합니다.  
구글링을 통해 내용 취합 및 공부를 하기 때문에 출처는 해당 Post 하단 부분 참고 부탁드립니다. 


# 1. 시계열 데이터는 무엇인가?

시계열(time series) 데이터는 관측치가 시간적 순서를 가진 데이터입니다.<sup>[1](#references)</sup> 일반적으로 시계열 데이터는 추세변동, 순환변동, 계절변동, 불규칙변동 요인으로 구성됩니다.<sup>[2](#references)</sup>  

> **추세변동(trend variation)**  
> : 장기간에 걸쳐 지속적으로 증가 또는 감소하거나 혹은 일정한 상태를 유지하려는 변동요인을 의미합니다.  
> **순환변동(cyclical variation)**  
> : 일정한 기간의 주기로 순환적으로(예를들어 상하로 반복되는 변동) 추세선을 따라 변화하는 변동요인을 의미합니다.  
> **계절변동(seasonal variation)**  
> : 보통 계절을 주기로 발생하는 변동요인을 의미하지만, 순환변동과 다른 점은 순환주기가 짧다는 것입니다.  
> **불규칙변동(irregular variation)**  
> : 어떤 규칙성이 없이 옟측 불가능하게 우연적으로 발생하는 변동요인을 의미합니다.  


# 2. 각 변동요인을 예측할 수 있을까?

주식, 물가만 봐도 각 변동요인을 예측한다는 것은 쉬운 일이 아니라는 것을 금방 알아차릴 수 있습니다. 즉, 시계열 데이터는 변동이 심해 평탄하고 변화가 완만한 값으로 변환시키는 평활(smoothing)화 처리가 필요합니다. 주요 평활법에는 이동평균법, 지수평활법, 홀트-윈터스 모형, 분해법 등이 있습니다. 

# 참고 자료 출처

<a name="references">1</a> : https://kyounju.tistory.com/25  
<a name="references">2</a> : http://www.aistudy.com/math/timeseries_lee.htm