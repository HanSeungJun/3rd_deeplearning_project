# 손동작 인식 기반 Human-Robot Interaction (ROS2)

사람의 손동작으로 주행로봇을 제어하는 시스템. 손동작을 인식해 명령으로 바꾸고, 로봇은 주행 라인과 장애물을 인식해 **그 명령을 수행할 수 있는지 스스로 판단**한다.

> 이 저장소는 팀 프로젝트 중 **제스처 인식 파트**(데이터 수집 · RNN 학습 · 검증)를 담고 있다.
> 전체 시스템 저장소: [addinedu-ros-3rd/deeplearning-repo-1](https://github.com/addinedu-ros-3rd/deeplearning-repo-1)

**▶ [데모 영상](https://youtu.be/fBUlsuLVDTE)**

![시스템 구성](https://github.com/HanSeungJun/calculator_pyqt/assets/81555330/13648217-e761-4c88-aa39-ade0f8552f87)

---

## 프로젝트 개요

1. 사람의 제스처(손·몸)를 인식해 주행로봇에 전달한다
2. 주행로봇은 라인과 장애물을 인식해 직진 / 좌회전 / 우회전 가능 여부를 판단한다
3. Ursina 3D 시뮬레이션과 ROS2 Gazebo에서 검증한 뒤 실제 주행로봇으로 옮긴다

**기간** 2023.11.25 ~ 2023.12.14 · **인원** 3명

| 구분 | 이름 | 역할 |
|---|---|---|
| 팀장 | 한승준 | 전체 시스템 구성도, 주행로봇 제작, Ursina 3D 시뮬레이션, 라인·장애물 인식 모듈 |
| 팀원 | 김창미 | 제스처 인식 모델 제작 및 성능 분석(KNN·LSTM·RNN), 제스처 인식 모듈, 시퀀스 다이어그램 |
| 팀원 | 박한규 | Semantic segmentation 모델(YOLOv5 · YOLOv8) |

---

## 제스처 명령 (8종)

Mediapipe로 추출한 손 랜드마크 시퀀스를 학습해 아래 8개 클래스로 분류한다.

| 클래스 | 의미 |
|---|---|
| `go` | 직진 |
| `back` | 후진 |
| `stop` | 정지 |
| `left_spin` / `right_spin` | 좌/우 회전 |
| `speed_up` / `speed_down` | 속도 증가/감소 |
| `bad_gesture` | 명령에 해당하지 않는 동작 |

동작 정의 이미지는 [`data/specifying_gestures/`](data/specifying_gestures)에 있다.

---

## 데이터셋

클래스당 샘플 수를 달리한 **두 벌**을 수집해 학습량이 성능에 미치는 영향을 비교했다.

| 데이터셋 | 클래스당 샘플 | 경로 |
|---|:---:|---|
| `dataset_10_231211` | 10 | [`data/dataset_10_231211/`](data/dataset_10_231211) |
| `dataset_100_231211` | 100 | [`data/dataset_100_231211/`](data/dataset_100_231211) |

각 클래스별 CSV와 이를 합친 `total_*.csv`가 함께 들어 있다.

---

## 모델

| 파일 | 학습 데이터 | epoch |
|---|---|:---:|
| [`model/RNN_model_dataset10_epoch500_231211.h5`](model) | 클래스당 10개 | 500 |
| [`model/RNN_model_dataset100_epoch500_231211.h5`](model) | 클래스당 100개 | 500 |

학습 코드: [`train/hand_gesture_recognition.ipynb`](train/hand_gesture_recognition.ipynb)

---

## 저장소 구조

```
data/
  specifying_gestures/     제스처 정의 이미지 (기본 8종 + 회전/각속도 변형)
  dataset_10_231211/       클래스당 10샘플 데이터셋
  dataset_100_231211/      클래스당 100샘플 데이터셋
model/                     학습된 RNN 모델 (.h5)
train/
  hand_gesture_recognition.ipynb   데이터 로드 · RNN 학습 · 평가
test/
  Pose_Estimation_to_keyboard_test.ipynb   포즈 추정 → 키보드 입력 매핑 검증
  g_r_y / g_y_r / r_g_y / r_y_g / y_g_r / y_r_g   순서 조합별 검증 노트북
```

---

## 기술 스택

`Python` `TensorFlow/Keras` `Mediapipe` `OpenCV` `ROS2` `YOLOv5/v8` `Ursina` `Arduino` `Qt`

---

## 실행

```bash
pip install mediapipe opencv-python tensorflow ursina ultralytics
jupyter notebook train/hand_gesture_recognition.ipynb
```
