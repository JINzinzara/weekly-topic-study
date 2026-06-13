# Week 07 | YOLO · mAP

---

## 목차
- [Topic 1. YOLO(You Only Look Once) 모델의 주요 특징과 장점](#topic-1)
- [Topic 2. mAP(mean Average Precision)의 개념과 활용](#topic-2)

---

<a name="topic-1"></a>
## Topic 1. YOLO(You Only Look Once) 모델의 주요 특징과 장점

### 1. 핵심 개념 요약




### 2. 상세 내용

#### YOLO란?
- **정의:**
- **등장 배경:**

#### 작동 방식
-
-

#### 주요 특징
| 특징 | 설명 |
|------|------|
| 단일 신경망 | |
| 실시간 처리 | |
| 그리드 기반 예측 | |
| Bounding Box 예측 | |

#### YOLO 버전별 발전
| 버전 | 주요 개선점 |
|------|-----------|
| YOLOv1 | |
| YOLOv3 | |
| YOLOv5 | |
| YOLOv8 | |

#### YOLO vs 기존 객체 탐지 모델 비교
| 구분 | YOLO | R-CNN 계열 |
|------|------|-----------|
| 처리 방식 | One-stage | Two-stage |
| 속도 | | |
| 정확도 | | |
| 실시간 적용 | | |

### 3. 왜 중요한가?
-
-

### 4. 참고 자료
-

---

<a name="topic-2"></a>
## Topic 2. mAP(mean Average Precision)의 개념과 활용

### 1. 핵심 개념 요약




### 2. 상세 내용

#### mAP란?
- **정의:**
- **왜 사용하나:**

#### 핵심 개념 정리

##### Precision & Recall
| 개념 | 정의 | 수식 |
|------|------|------|
| Precision (정밀도) | | |
| Recall (재현율) | | |

##### IoU (Intersection over Union)
- **정의:**
- **역할:**
- **임계값(Threshold) 기준:**

##### AP (Average Precision)
- **정의:**
- **계산 방법:**

##### mAP (mean Average Precision)
- **정의:**
- **계산 방법:**

#### mAP 계산 흐름
- IoU 기준으로 TP / FP 판별
- 클래스별 Precision-Recall 곡선 생성
- 각 클래스의 AP 계산
- 전체 클래스 AP의 평균 → mAP

#### mAP 값 해석
| mAP 범위 | 의미 |
|---------|------|
| 0.5 이상 | |
| 0.75 이상 | |
| mAP@0.5 | |
| mAP@0.5:0.95 | |

### 3. 왜 중요한가?
-
-

### 4. 참고 자료
-
