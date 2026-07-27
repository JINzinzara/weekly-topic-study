# Week 10 | 텍스트 전처리 · Word Embedding · Attention · Transformer

---

## 목차
- [Topic 1. 텍스트 데이터 전처리 과정](#topic-1)
- [Topic 2. FastText와 Word2Vec의 차이 및 장점](#topic-2)
- [Topic 3. Attention 메커니즘이 해결하는 Seq2Seq의 문제](#topic-3)
- [Topic 4. Transformer와 Seq2Seq 구조의 근본적 차이](#topic-4)

---

<a name="topic-1"></a>
## Topic 1. 텍스트 데이터 전처리 과정

### 1. 핵심 개념 요약
자연어 처리에서의 전처리 과정은 컴퓨터가 텍스트를 이해할 수 있도록 다듬는 단계로,
정제 &rarr; 토큰화 &rarr; 인코딩의 순서로 진행된다.

### 2. 상세 내용

#### (정제 및 정규화)
- 노이즈 제거: 특수문자, HTML 태그, 불필요한 공백 제거
- 대소문자 통일: 문장이 영어 일 경우, 소문자나 대문자로 바꿈
- 불용어 제거: "은, 는, 이, 가, is, a"처럼 의미가 적은 단어를 제거

#### (토큰화)
- 문장 분리: 긴 글을 문장 단위로 split
- 단어/형태소 분리: 한국어의 경우 의미가 있는 최소 단위인 형태소 자르며, 영문자는 단어 단위로 자름

#### (인코딩 및 벡터화)
- 정수 인코딩: 각 단어에 인덱스(정수)를 붙인다 = 어휘 사전 생성
- 패딩: 패딩을 추가하며 문장들의 길이를 맞춤
- 벡터화: 단어를 숫자로 된 묶음으로 바꾼다 &rarr; 임베딩

---

<a name="topic-2"></a>
## Topic 2. FastText와 Word2Vec의 차이 및 장점

### 1. 핵심 개념 요약
임베딩 모델에는 크게 Word2Vec, FastText, GloVe가 있다.
Word2Vec의 OOV, 현태 변화에 약하다는 단점을 보완 하고자 나온 모델이 FastText과 GloVe이다.

### 2. 상세 내용

#### (Word2Vec)
- 분포 가설을 기반으로 둔 임베딩 모델로, 주변 단어와 중심 단어를 서로 맞히는 문제를 학습
- "주변 단어를 통해 중심 단어 예측" 은 중심 단어 주변의 단어들을 슬라이딩 윈도우를 통해 예측
- CBOW: 주변 단어 &rarr; 중심 단어
- Skip-gram: 중심 단어 &rarr; 주변 단어
- 지가지도(Self-supervised) 학습

#### (FastText)
- OOV, 형태 변화에 약한 Word2Vec 단점 보완
- 단어를 서브워드로 잘게 쪼개어 다룸

#### Word2Vec vs FastText 비교
| 구분 | Word2Vec | FastText |
|------|----------|----------|
| 학습 단위 | 단어 전체 | 서브워드(단어보다 더 작은 단위) |
| 벡터 구성 | 단어 자체를 임베딩 | 해당 단어를 구성하는 서브워드 벡터들의 합(또는 평균) |
| OOV처리 | X | O |
| 형태 변환 | X | O |

### 3. 참고 자료
- https://jaeyoon-95.tistory.com/232

---

<a name="topic-3"></a>
## Topic 3. Attention 메커니즘이 해결하는 Seq2Seq의 문제

### 1. 핵심 개념 요약
Seq2Seq의 병목 현상과 장기 의존성을 해결하기 위해,
시점별로 중요한 부분에 집중하는 Attention이 도입되었다.

### 2. 상세 내용

#### (병목 현상)
- Seq2Seq은 모든 문장을 하나의 context vector로 압축하기 때문에,
  문장이 길어질 수록 앞 정보가 흐려지며 번역의 품질 저하

#### (장기 의존성)
- 입력 문장이 길어질 수록 디코더가 문장 초반의 정보를 제대로 활용하지 못함

#### (Attention의 특징)
- 모든 시점에서의 hidden state를 바라보기 때문에,
  디코더가 단어를 생성할 때 바로바로 필요한 부분에 집중
- 현재 디코더와 인코더 시점 간의 유사도를 계산하여 가중치 구함
  &rarr; 가중치로 인코더의 hidden state를 가중합 하여 시점별 context vector 생성

---

<a name="topic-4"></a>
## Topic 4. Transformer와 Seq2Seq 구조의 근본적 차이

### 1. 핵심 개념 요약
Seq2Seq + Attention은 RNN 구조로 Attention이 보조 역할을 한다.
반면 Transformer은 RNN 구조를 제거하고 Attention 자체를 핵심 메커니즘으로 삼는다.

### 2. 상세 내용

#### Seq2Seq(+Attention) vs Transformer 비교
| 구분 | Seq2Seq (+Attention) | Transformer |
|------|----------------------|-------------|
| 시퀀스 처리 방식 | 순차적(RNN) | 시퀀스 전체를 한 번에 |
| 병렬화 | 순차적 학습으로 인해 병렬화가 어려움 | 시퀀스 내 모든 위치를 동시에 계산 가능 |
| 장기 의존성 | O | X |
| 위치 정보 | RNN의 순차적 학습으로 위치 정보 보유 | 순서 정보 별도 처리 필요(Positinal Encoding)
| Attention의 역할 | Cross-Attention, 보조적 역할 | 인코더/디코더 내부에서도 핵심 연산이 됨 |
