# AI Agent

## 1. AI Agent란?
AI Agent는 환경을 인지하고 정보를 처리하며 목표를 달성하기 위해 **인간의 개입 없이** 행동할 수 있는 소프트웨어 프로그램

## 2. AI Agent의 주요 특징
  - Autonomy(자율성)
    : 최소한의 또는 인간의 개입 없이 스스로 운영
  - Perception(지각)
    : 여러 형태의 데이터(텍스트, 음성, 이미지, 구조화된 데이터)에서 정보를 수집
  - Decision-making(의사 결정)
    : 데이터를 분석하고 최선의 행동 방침을 결정
  - Adaptability(적응력)
    : 상호작용을 통해 학습하고 시간이 지남에 따라 성장

## 3. AI Agent의 종류

1. **Reactive Agents** - 가장 단순한 형태의 AI
  - 정해진 규칙에 따라 운영 됨. 
  - 과거 경험을 저장하지 않음
  - 성장 가능성 없음
  - 규칙 기반 작업에 용이
  - 예) 스팸메일 분류, NPC와 같은 게임 내 기본 AI, 자율 센서(모션 감지기)

2. **Limited Memory Agent** - 과거 상호작용을 통해 학습
  - 의사결정 개선을 위해 과거 데이터를 단기 보존
  - 장기적 경험으로의 성장 불가능
  - 오늘날 대부분의 AI 시스템(실시간 반응 + 단기 학습)
  - 예) 챗봇, 자율주행차, AI기반 고객 지원

3. **Goal-Based Agents** - 목표 달성을 위한 행동 평가
  - 결정을 내리기 전에 여러 가능성에 대해 평가
  - 검색 알고리즘과 의사결정 트리를 사용해 최선의 행동 결정
  - 과거의 상호작용 + 미래의 결과 예측
  - 예) 알파고와 같은 게임 속 예측 AI, 네비게이션 시스템, Robo-advisors(금융)

4. **Learning Agents**
  - ML, DL을 활용한 경험을 바탕으로 지속적인 개선
  - RL(Reinforcement Learning: 보상 학습)을 통한 피드백으로 개선
  - 대규모 데이터셋 + 과거 경험 -> 다양한 의사결정
  - 예) 추천 시스템, AI 어시스턴트, 자율 로봇

## 4. Agentic AI 구축 - 7단계
1. **AI Agent의 목적 정의**
  - 해결하고자 하는 문제
  - 사용자 정의
  - 입력의 형태
  - 최종 결정
  - 자율성의 정도
  - AI Agent 유형 선택
    - 규칙 기반 작업 -> Reactive Agent
    - 단기 학습 -> Limited Memory Agent
    - 복잡한 의사결정 -> Goal-Based Agent
    - 지속적인 학습 -> Learning Agent
  
2. **적절한 도구와 프레임워크 선택**

  2-1. **도구 선택**
  - Python - 가장 많이 사용
      : AI 기반 챗봇, 추천 시스템, 예측 분석, NLP 기반 에이전트, 딥러닝 애플리케이션
  - JavaScript - 웹 기반 AI 애플리케이션에 적합
      : AI 기반 챗봇, 웹 기반 비서, 브라우저 기반 AI 도구
  - Java - 기업용 AI 애플리케이션
      : AI 기반 사기 탐지, 자동화 도구, 그리고 엔터프라이즈급 AI 에이전트
  - C++ - 실시간 애플리케이션을 위한 고성능 AI
      : AI 기반 자율주행차, 로봇공학, 그리고 게임 AI

  2-2. **AI 라이브러리 및 프레임 워크**
  
    2-2-1. 자연어 처리(NLP)
    - NLTK(Natural Language Toolkit: 자연어 툴킷): 토큰화, 음성 태깅, 텍스트 분류 도구
    - spaCy: 실시간 NLP 애플리케이션에 적합
    - Transformers (by Hugging Face): 사전 학습된 AI 모델(GPT, BERT, T5 등)과 통합 가능
    
    2-2-2. ML 및 모델 학습
    - TensorFlow: 복잡한 AI모델 학습 및 배포
    - PyTorch: AI 연구 및 첨단 머신러닝 응용
    - Scikit-learn: 분류, 회귀, 클러스터링 같은 전통적인 머신러닝 알고리즘
    
    2-2-3. 컴퓨터 비전(CV)
    - 
    https://wikidocs.net/323768
