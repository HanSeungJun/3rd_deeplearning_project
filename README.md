# Human-Robot Interaction System with ROS2
![3rd_final](https://github.com/HanSeungJun/calculator_pyqt/assets/81555330/c1faacbb-51a2-4588-b169-8337f4d90010)

## 시스템 구성
![image](https://github.com/HanSeungJun/calculator_pyqt/assets/81555330/13648217-e761-4c88-aa39-ade0f8552f87)

## 시퀀스 다이어그램
### 직진 케이스
![Screenshot from 2023-12-18 18-07-20](https://github.com/HanSeungJun/calculator_pyqt/assets/81555330/4c751f0b-7f6b-45ae-a65d-5a734c425fb6)

### 직진 불가 케이스

## 팀원 소개 및 역할
|구분|이름|역할|
|---|---|---|
|팀장|한승준|전체 시스템 구성도 제작, 주행로봇 제작, Ursina: 3D simulation game 제작, 라인 및 장애물 인식 모듈 제작|
|팀원|김창미|제스처 인식 인공지능 모델 제작 및 성능분석(KNN, LSTM, RNN), 제스처 인식 모듈 구현, 시퀀스 다이어그램 제작|
|팀원|박한규|Semantic segementation 모델(yolov5 & yolov8) 제작|

## 프로젝트 기간
2023.11.25 ~ 2023.12.14

## 기술 스택
### 개발환경
![Visual Studio Code](https://img.shields.io/badge/Visual%20Studio%20Code-007ACC?style=for-the-badge&logo=Visual%20Studio%20Code&logoColor=white)
![Arduino](https://img.shields.io/badge/arduino-00878F?style=for-the-badge&logo=arduino&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=Git&logoColor=white)
![Github](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=GitHub&logoColor=white)
![RDS](https://img.shields.io/badge/AWS%20RDS-527FFF?style=for-the-badge&logo=Amazon%20RDS&logoColor=white)
![Qt](https://img.shields.io/badge/Qt-41CD52?style=for-the-badge&logo=Qt&logoColor=white)
![mitapp](https://github.com/addinedu-ros-3rd/iot-repo-2/assets/81555330/11db2c8f-f4ae-46c0-ae71-d83b6e9e1d5c)
</div>

### 언어
![C++](https://img.shields.io/badge/c++-00599C?style=for-the-badge&logo=c%2B%2B&logoColor=white)
![Python](https://img.shields.io/badge/python-3776AB?style=for-the-badge&logo=python&logoColor=white)

### 커뮤니케이션
![Slack](https://img.shields.io/badge/slack-4A154B?style=for-the-badge&logo=slack&logoColor=white)

## 프로젝트 소개
### Human-Robot Interaction System with ROS2

1. 사람의 제스처(손, 몸)를 인식하고 주행로봇에게 전달한다.
2. 주행로봇은 라인 및 장애물을 인식하고 직진, 좌회전, 우회전 가능 여부를 판단할 수 있다.
3. ROS2 gazebo simulation을 통해 1번과 2번을 검증을 해보고 실제 주행로봇에게 전달해본다.

## 프로젝트 목표
머신러닝과 딥러닝 모델 직접 만들기
- 데이터셋 수집
- 머신러닝, 딥러닝 모델 학습
- 모델 간의 성능 비교 및 평가

## Hand landmarks detection
### Mediapipe
머신러닝
- KNN 모델
  
딥러닝
- LSTM 모델
- RNN 모델

## Semantic segmentation 
Yolov5
- contents

Yolov8
- contents

## Requirement
```
ursina
ultralytics
opencv-python

```
## How to run?
- Download
```
$ git clone https://github.com/addinedu-ros-3rd/deeplearning-repo-1.git
```

- Hands detect system
```
$ cd hands_detect_system
```

- Line detect system
```
$ cd yolov5

# 내장,외부 웹캠 source = 0, 1, 2 ...
$ yolo segment predict model=~/yolov5/runs/segment/train/weights/best.pt source=0

# 동영상 
$ yolo segment predict model=~/yolov5/runs/segment/train/weights/best.pt source=<vdeio path> 
```

- Minecraft simulation
```
$ cd minecraft_simulation

$ pip install ursina

$ python3 menu.py 
```

## Demo video
<p align=center>
  <a href="https://youtu.be/fBUlsuLVDTE?si=vuUHYnaWxRCwBf6v">
    <img src="https://i.ytimg.com/an_webp/fBUlsuLVDTE/mqdefault_6s.webp?du=3000&sqp=CPKZ5asG&rs=AOn4CLAQ-l7DkMBIoFy6Bmuyb-yrfhNSKw" width="40%">
  </a>
  <br>
  <a href="https://youtu.be/fBUlsuLVDTE?si=vuUHYnaWxRCwBf6v">1차 데모영상</a>
</p>

## 회고
-
-
