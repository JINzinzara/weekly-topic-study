# Week 09 | Semantic Segmentation · FCN · GAN · Diffusion

---

## 목차
- [Topic 1. Semantic Segmentation과 이미지 분류의 차이](#topic-1)
- [Topic 2. FCN(Fully Convolutional Networks)의 특징](#topic-2)
- [Topic 3. GAN의 생성자(Generator)와 판별자(Discriminator)](#topic-3)
- [Topic 4. Diffusion 모델의 이미지 생성 활용과 장점](#topic-4)

---

<a name="topic-1"></a>
## Topic 1. Semantic Segmentation과 이미지 분류의 차이

### 1. 핵심 개념 요약
컴퓨터 비전에는 이미지 분류, 객체 인식, 이미지 분할, 이미지 생성 등 다양한 영역들이 존재한다.
그 중 Segmantic은 이미지 분할로 특정 물체를 박스가 아닌 픽셀 단위로 인식하고 분할하는 방식이다.
Segmantic은 3 종류로 나뉜다. 동일한 클래스끼리 묶는 Semantic과 객체별로 나누어 분할하는 Instance,
Semantic과 Instance를 합친 Panoptic이 있다.

### 2. 상세 내용

#### Semantic Segmentation이란?
- **정의:** 이미지 분할(segmentation)의 한 종류로, 픽셀마다 어떤 클래스인지를 분할한다
- **출력 형태:** 물체의 픽셀 단위 윤곽/ sematic은 동일한 클래스들끼리 영역
- **활용 분야:** 의료 영상에서 종양의 영역을 찾아낼 때 용이하다

#### 이미지 분류(Classification)란?
- **정의:** 이미지를 특정 클래스에 따라 분류하는 것이다
- **출력 형태:** 하나의 라벨
- **활용 분야:** 의료 영상에서 질환의 유무를 분류할 때 용이하다

#### Semantic Segmentation vs Classification 비교
| 구분 | Semantic Segmentation | Classification |
|------|----------------------|----------------|
| 출력 단위 | 픽셀 단위 | 이미지 단위 |
| 출력 형태 | 픽셀 단위 윤곽 | 하나의 라벨 |
| 목적 | 클래스별 분할 | 클래스 분류 |

#### 관련 개념 비교 (Segmentation 종류)
| 종류 | 설명 |
|------|------|
| Semantic Segmentation | 픽셀마다 어떤 클래스인지 분할; 같은 클래스일 경우 하나의 색으로 표시 |
| Instance Segmentation | 픽셀마다 객체에 따라 분할; 같은 클래스여도 다른 객체일 경우, 다른 색으로 표시 |
| Panoptic Segmentation | 배경에 대해서 Semantic, 객체 구분할 때는 Instance |

---

<a name="topic-2"></a>
## Topic 2. FCN(Fully Convolutional Networks)의 특징

### 1. 핵심 개념 요약
FCN은 CNN의 위치정보 소실과 특징맵 크기 복원 불가의 한계를 극복하고자 만들어진, 모든 레이어가 합성곱 연산으로 이루오진 신경망이다.
FC를 Convolution 레이어로 바꿈으로써, 위치 정보를 보존하고, 입력 크기가 달라도 동작 가능하다. 
또한 인코더와 디코더 사이에 Skip Connection을 통해 이미지의 디테일을 보존한다.

### 2. 상세 내용

#### FCN이란?
- **정의:** 모든 레이어가 합성곱 연산으로 이루어진 신경망
- **등장 배경:**
CNN의 한계
1. 마지막 FC층에서 flatten 하는 과정에서 이미지의 위치 정보의 소실
2. 특징맵 크기 원상 복구 어려움

#### FCN의 주요 특징
| 특징 | 설명 |
|------|------|
| Fully Connected Layer 제거 | 이미지의 위치 정보를 보존 |
| 1x1 Convolution 사용 | CNN의 FC층과 다르게 입력 크기가 달라도 동작하며, 위치 정보를 포함 |
| Upsampling (Deconvolution) | 특징맵의 크기를 원본 크기로 업샘플링 |
| Skip Connection | 깊은 레이어(추상적)와 얕은 레이어(디테일)를 합쳐서 사용 |

#### 기존 CNN 기반 분류 모델과의 차이
| 구분 | 기존 CNN (분류용) | FCN |
|------|------------------|-----|
| 마지막 레이어 | Fully Connected Layer | Convolutional Layer |
| 입력 이미지 크기 | 고정 | 가변 가능 |
| 출력 형태 | 클래스 확률 (1차원) | 픽셀별 클래스 맵 (2차원) |
| 공간 정보 | 손실됨 | 유지됨 |

### 3. 참고 자료
- https://wikidocs.net/128393

---

<a name="topic-3"></a>
## Topic 3. GAN의 생성자(Generator)와 판별자(Discriminator)

### 1. 핵심 개념 요약
GAN은 학습 데이터를 통해 현실적인 새로운 데이터를 생성하는 모델로, 
생성자가 가짜 이미지를 만들고 판별자를 속이는 과정에서 생성자는 더욱 현실적이고 진짜같은 데이터를 생성하게 된다

### 2. 상세 내용

#### GAN(Generative Adversarial Network)이란?
- **정의:** 기존 데이터 학습을 통해 현실적인 새로운 데이터를 생성하는 모델
- **핵심 아이디어 (적대적 학습):** 생성자와 판별자 두 신경망이 경쟁을 하며 학습

#### Generator vs Discriminator 비교
| 구분 | Generator | Discriminator |
|------|-----------|---------------|
| 역할 | 랜덤 노이즈를 통해 진짜 이미지 같은 가짜 이미지를 생성 | 이미지가 진짜인지 가짜인지 가려냄 |
| 입력 | 랜덤 노이즈 이미지 | 실제 학습 데이터 + 가짜 데이터 |
| 출력 | 가짜 이미지 | 입력이 진짜일 확률 |
| 목표 | 판별자를 속이는 가짜 데이터 생성 | 진짜/가짜를 정확히 구분 |

#### GAN의 학습 과정
1. 생성자가 가짜 이미지를 생성
2. 판별자가 진짜 이미지와 가짜 이미지를 통해 진짜일 확률을 출력
3. 판별자가 이기면 똑똑해지고, 생성자가 이기면 생성자는 보상을 받고 판별자는 패널티를 받음
4. 생성자는 더 진짜 같은 가짜 이미지를, 판별자는 더 정확한 분류가 가능해지도록 학습
5. 판별자가 구분하지 못할 정도의 현실적이고 진짜 같은 이미지를 생성자가 생성

### 3. 왜 중요한가?
- 비지도 학습으로, 라벨링이 필요하지 않음

### 4. 참고 자료
- https://www.geeksforgeeks.org/deep-learning/generative-adversarial-network-gan/

---

<a name="topic-4"></a>
## Topic 4. Diffusion 모델의 이미지 생성 활용과 장점

### 1. 핵심 개념 요약




### 2. 상세 내용

#### Diffusion 모델이란?
- **정의:** 학습 이미지에 무작위 노이즈를 점진적으로 확산(diffusion) 시킨 후, 역으로 노이즈를 제거하는 학습을 통해 새로운 이미지를 생성
- **핵심 아이디어:** 이미지에 노이즈를 천천히 추가하여 완전히 노이즈 처리가 된 후, 역으로 노이즈를 제거하는 것만으로도 새로운 이미지 생성 가능

#### 작동 방식
| 단계 | 설명 |
|------|------|
| Forward Process (노이즈 추가) | 깨끗한 학습 이미지에 가우시안 노이즈를 점진적으로 추가 |
| Reverse Process (노이즈 제거) | 노이즈 추가 과정을 역으로 수행하여서 디노이징 학습을 통해 새로운 이미지 생성 |

#### 이미지 생성에서의 활용
- 텍스트로 그림 그려주는 모델(GPT, DALL-E, Stable Diffusion 등)

#### Diffusion 모델의 장점
| 장점 | 설명 |
|------|------|
| 학습 안정성 | 높음 |
| 생성 품질 | 높음 |
| 다양성 | 높음(무작위 노이즈 역할) |

#### GAN vs Diffusion 비교
| 구분 | GAN | Diffusion |
|------|-----|-----------|
| 학습 안정성 | 낮음| 높음 |
| 생성 속도 | 빠름 | 느림 |
| 생성 품질 | 높음(편차가 심함) | 높음 |

### 3. 참고 자료
- https://www.ibm.com/think/topics/diffusion-models
