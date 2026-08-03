# Week 11 | BERT · GPT · Hugging Face · 사전학습 모델

---

## 목차
- [Topic 1. BERT와 GPT의 주요 차이점](#topic-1)
- [Topic 2. Hugging Face Transformers 라이브러리](#topic-2)
- [Topic 3. BERT·GPT 이후 등장한 주요 사전학습 모델](#topic-3)

---

<a name="topic-1"></a>
## Topic 1. BERT와 GPT의 주요 차이점

### 1. 핵심 개념 요약
BERT와 GPT는 트랜스포머에서 파생된 NLP 모델로, 각각 트랜스포머의 인코더와 디코더의 특징을 가진다.
BERT는 인코더를 사용하여 문장의 전체를 이해하는 것에 특화되어 있으며,
GPT는 디코더를 사용하여 생성에 특화되어 있다.

### 2. 상세 내용

#### BERT란?
: Bidirectional Encoder Representations from Transformers
트랜스포머의 인코더 스택만을 사용하여, 문장 전체를 양방향으로 보고 이해

#### GPT란?
: Generative Pre-trained Transformer
트랜스포머의 디코더 스택만 사용하여, 앞말을 통해 뒷말을 예측

#### BERT vs GPT 비교
| 구분 | BERT | GPT |
|------|------|-----|
| 기본 구조 | 인코더 | 디코더 |
| 작동 방식 | 양방향성 | 단방향성 |
| 학습 방식 | mask로 단어 예측 | 다음 단어 예측 |
| 적합한 응용 분야 | 이해(감정 분석) | 생성(요약, 번역) |

---

<a name="topic-2"></a>
## Topic 2. Hugging Face Transformers 라이브러리

### 1. 핵심 개념 요약
Hugging Face를 통해 직접 학습 코드와 데이터를 통해 모델 학습 시킬 것 없이,
사전 학습된 모델을 로드하여 자신에게 맞게 Fine-tuning하여 사용 가능하다.

### 2. 상세 내용

#### Hugging Face Transformers란?
- Hugging Face: 세계에서 다양한 연구자들이 대량의 데이터를 통해 사전학습된 모델을 모아둔 라이브러리

#### 주요 제공 기능
| 기능 | 설명 |
|------|------|
| Auto 클래스(AutoModel, AutoTokenizer) | 이름 변경만으로 수백 개의 모델을 동일한 방식으로 로드 |
| Pipeline API | 전처리, 추론, 후처리 할 것 없이 바로 추론 결과 도출 |
| Trainer API(Fine-tuning) | 사전학습된 모델을 내 데이터에 맞게 자동 조절 |

---

<a name="topic-3"></a>
## Topic 3. BERT·GPT 이후 등장한 주요 사전학습 모델

### 1. 핵심 개념 요약
BERT와 GPT이후 트랜스포머의 인코더와 디코더를 함께 사용 가능한 모델이 등장하게 되었고,
대표적으로 BART와 T5가 있다.

### 2. 상세 내용

#### 모델 1: (BART)
- Denoising(잡음 제거) 방식으로 학습
- 손상된 원문을 복원하는 과정을 학습하여, 문장 생성에 특화

#### 모델 2: (T5)
- 모든 과제의 입력과 출력을 "텍스트"로 통일
- 따로 층을 추가하기 보다는 입력 받은 텍스트 앞에 지시문(CLS)을 추가하여 해당 과제를 수행
- 하나의 모델로 여러 과제 수행 가능
