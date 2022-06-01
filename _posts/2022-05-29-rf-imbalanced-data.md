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

## Abstract

본 논문에서는 random forest를 이용해 불균형 데이터의 분류 문제를 다루는 2가지 방법을 제안합니다. 하나는 cost sensitive learning을 기반으로 하고 다른 하나는 샘플링 기술을 기반으로 합니다. 분류 성능 평가지표로 precision과 recall, false positive rate와 false negative rate, F-measure와 weighted accuracy가 계산됩니다. 두 방법은 minority 클래스에 대한 예측 정확도 향상과 기존 알고리즘과 비교해서 좋은 성능을 보였습니다.  

## 1. Introduction

많은 실제 분류 문제가 불균형합니다. 즉, 클래스 중 적어도 하나는 아주 작은 소수의 데이터. 이러한 문제의 경우 관심은 일반적으로 희귀 클래스(우리는 "positive" 클래스라고 부를 것입니다)에 대한 올바른 분류로 기울입니다. 예를들어 fraud detection, network intrusion, rare disease 등이 있습니다. 그런나 가장 일반적으로 사용된는 분류 알고리즘은 positive 클래스에 특별한 주의를 기울이기보다 전체 오류율을 최소화하는 것을 목표로 하기 때문에 이러한 문제에 잘 작동하지 않습니다.  
극도로 불균형한 데이터 문제를 해결하기 위한 두 가지 일반적인 접근 방식이 있습니다. 하나는 소수 계층의 오분류에 높은 비용을 할당하고 전체 비용을 최소화하려고 하는 cost sensitive learning을 기반으로 합니다. 다른 접근 방식은 다수 클래스를 다운 샘플링하거나 소수 클래스를 오버 샘플링하거나 둘 다 하는 샘플링 기술을 사용하는 것입니다.  
본 연구에서는 RF 알고리즘을 기반으로 극단적인 불균형 문제를 처리하는 두 가지 방법을 제안합니다. 하나는 클래스 가중치를 RF 분류기에 통합하여 비용에 민감하게 만들고 소수 클래스를 잘못 분류하는 데 벌점을 줍니다. 다른 하나는 샘플링 기법과 앙상블 아이디어를 결합한 것입니다.  

## 2. Methodology

### 2.2. Balanced Random Forest

RF는 학습데이터의 부트스트랩 샘플에서 각 구성 트리를 유도합니다. 극심한 불균형 데이터 학습에서는 그 부트스트랩에 소수 클래스가 없거나 적게 포함되기 때문에 소수 클래스에 대한 예측 성능이 떨어지는 결과로 이어집니다. 이 문제를 해결하기 위해 계층화된 부트스트랩을 사용합니다.  

(1) RF의 각 반복에 대해 소수 클래스에서 부트스트랩 샘플을 추출합니다. 다수 클래스에서 교체와 함께 동일한 수의 케이스를 무작위로 추출합니다.  
(2) pruning 없이 데이터에서 최대 크기로 분류 트리를 유도합니다. 트리는 다음 수정과 함께 CART 알고리즘으로 유도됩니다. 최적 분할을 위해 모든 변수를 검색하는 대신 각 노드에서 무작위로 선택된 변수 세트만 검색합니다.  
(3) 원하는 횟수만큼 위의 두 단계를 반복합니다. 앙상블의 예측을 집계하여 최종 예측을 합니다.  

### 2.3. Weighted Random Forest

RF 분류기는 다수 클래스로 편향되는 경향이 있으므로 소수 클래스를 잘못 분류하는 경우 더 과한 벌점을 부과합니다. 각 클래스에 가중치를 할당하고 소수 클래스에 더 큰 가중치를 부여합니다. 클래스 가중치는 두 위치에서 RF 알고리즘에 통합됩니다. 트리 유도 절차에서 클래스 가중치는 분할을 찾기 위한 Gini 기준에 가중치를 부여하는 데 사용됩니다. 각 트리의 터미널 노드에서 클래스 가중치가 다시 고려됩니다. 

## 참고 자료 출처

<a name="references">1</a> : https://statistics.berkeley.edu/sites/default/files/tech-reports/666.pdf  
