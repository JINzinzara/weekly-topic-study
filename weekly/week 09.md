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




### 2. 상세 내용

#### Semantic Segmentation이란?
- **정의:**
- **출력 형태:**
- **활용 분야:**

#### 이미지 분류(Classification)란?
- **정의:**
- **출력 형태:**
- **활용 분야:**

#### Semantic Segmentation vs Classification 비교
| 구분 | Semantic Segmentation | Classification |
|------|----------------------|----------------|
| 출력 단위 | 픽셀 단위 | 이미지 단위 |
| 출력 형태 | | |
| 목적 | | |
| 활용 예시 | | |

#### 관련 개념 비교 (Segmentation 종류)
| 종류 | 설명 |
|------|------|
| Semantic Segmentation | |
| Instance Segmentation | |
| Panoptic Segmentation | |

### 3. 왜 중요한가?
-
-

### 4. 참고 자료
-

---

<a name="topic-2"></a>
## Topic 2. FCN(Fully Convolutional Networks)의 특징

### 1. 핵심 개념 요약




### 2. 상세 내용

#### FCN이란?
- **정의:**
- **등장 배경:**

#### FCN의 주요 특징
| 특징 | 설명 |
|------|------|
| Fully Connected Layer 제거 | |
| 1x1 Convolution 사용 | |
| Upsampling (Deconvolution) | |
| Skip Connection | |

#### 기존 CNN 기반 분류 모델과의 차이
| 구분 | 기존 CNN (분류용) | FCN |
|------|------------------|-----|
| 마지막 레이어 | Fully Connected Layer | Convolutional Layer |
| 입력 이미지 크기 | 고정 | 가변 가능 |
| 출력 형태 | 클래스 확률 (1차원) | 픽셀별 클래스 맵 (2차원) |
| 공간 정보 | 손실됨 | 유지됨 |

### 3. 왜 중요한가? 
-
-

### 4. 참고 자료
-

---

<a name="topic-3"></a>
## Topic 3. GAN의 생성자(Generator)와 판별자(Discriminator)

### 1. 핵심 개념 요약




### 2. 상세 내용

#### GAN(Generative Adversarial Network)이란?
- **정의:**
- **핵심 아이디어 (적대적 학습):**

#### 생성자 (Generator)
- **역할:**
- **입력:**
- **출력:**
- **학습 목표:**

#### 판별자 (Discriminator)
- **역할:**
- **입력:**
- **출력:**
- **학습 목표:**

#### Generator vs Discriminator 비교
| 구분 | Generator | Discriminator |
|------|-----------|---------------|
| 역할 | | |
| 입력 | | |
| 출력 | | |
| 목표 | 판별자를 속이는 가짜 데이터 생성 | 진짜/가짜를 정확히 구분 |

#### GAN의 학습 과정
-
-

### 3. 왜 중요한가?
-
-

### 4. 참고 자료
-

---

<a name="topic-4"></a>
## Topic 4. Diffusion 모델의 이미지 생성 활용과 장점

### 1. 핵심 개념 요약




### 2. 상세 내용

#### Diffusion 모델이란?
- **정의:**
- **핵심 아이디어:**

#### 작동 방식
| 단계 | 설명 |
|------|------|
| Forward Process (노이즈 추가) | |
| Reverse Process (노이즈 제거) | |

#### 이미지 생성에서의 활용
-
-

#### Diffusion 모델의 장점
| 장점 | 설명 |
|------|------|
| 학습 안정성 | |
| 생성 품질 | |
| 다양성 | |

#### GAN vs Diffusion 비교
| 구분 | GAN | Diffusion |
|------|-----|-----------|
| 학습 안정성 | | |
| 생성 속도 | | |
| 생성 품질 | | |
| 대표 모델 | | |

### 3. 왜 중요한가? 
-
-

### 4. 참고 자료
-
