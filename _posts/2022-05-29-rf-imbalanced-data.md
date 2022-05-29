---
layout: post
title: Paper - Using Random Forest to Learn Imbalanced Data
subtitle: summary
date: 2022-05-29
categories: paper
tags: [random-forest, imbalanced-data]
---

이번 글은 "Using Random Forest to Learn Imbalanced Data" 논문에 대한 요약을 목적으로 합니다.  
논문 출처는 하단 부분 참고 부탁드립니다.<sup>[1](#references)</sup>  

# Abstract

본 논문에서는 random forest를 이용해 불균형 데이터의 분류 문제를 다루는 2가지 방법을 제안합니다. 하나는 cost sensitive learning을 기반으로 하고 다른 하나는 샘플링 기술을 기반으로 합니다. 분류 성능 평가지표로 precision과 recall, false positive rate와 false negative rate, F-measure와 weighted accuracy가 계산됩니다. 두 방법은 minority 클래스에 대한 예측 정확도 향상과 기존 알고리즘과 비교해서 좋은 성능을 보였습니다.  

# 1. Introduction

많은 실제 분류 문제가 불균형합니다. 즉, 클래스 중 적어도 하나는 아주 작은 소수의 데이터. 이러한 문제의 경우 관심은 일반적으로 희귀 클래스(우리는 "positive" 클래스라고 부를 것입니다)에 대한 올바른 분류로 기울입니다. 예를들어 fraud detection, network intrusion, rare disease 등이 있습니다. 그런나 가장 일반적으로 사용된는 분류 알고리즘은 positive 클래스에 특별한 주의를 기울이기보다 전체 오류율을 최소화하는 것을 목표로 하기 때문에 이러한 문제에 잘 작동하지 않습니다.  
극도로 불균형한 데이터 문제를 해결하기 위한 두 가지 일반적인 접근 방식이 있습니다. 하나는 소수 계층의 오분류에 높은 비용을 할당하고 전체 비용을 최소화하려고 하는 cost sensitive learning을 기반으로 합니다. 다른 접근 방식은 다수 클래스를 다운 샘플링하거나 소수 클래스를 오버 샘플링하거나 둘 다 하는 샘플링 기술을 사용하는 것입니다. 

# 참고 자료 출처

<a name="references">1</a> : https://statistics.berkeley.edu/sites/default/files/tech-reports/666.pdf  
