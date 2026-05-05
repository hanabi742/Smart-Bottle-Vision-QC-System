# 🍼 CNN 기반 음료 용기 2단계 통합 품질관리 시스템 (Vision QC)

> **"데이터 부족의 한계를 기술로 극복한 스마트 팩토리 자동화 검사 솔루션"**
> 본 프로젝트는 입고부터 조립 완료까지의 공정을 CNN 모델(PatchCore, YOLO)과 MFC 관제 시스템으로 연결한 소프트웨어-하드웨어 통합 프로젝트입니다.

---

## 📺 프로젝트 시연 및 주요 화면

* 실시간 대시보드에서 검사 이력 및 서버 상태 확인
* 아두이노 연동을 통한 물리적 불량 배출 시스템 (LED 경고등)

---

## 🛠 주요 기술 스택 (Tech Stack)
- **Language:** C++, Python
- **Framework/Library:** MFC, PyTorch, OpenVINO, OpenCV[cite: 1]
- **AI Models:** PatchCore (1공정: 이상 탐지), YOLOv11 (2공정: 객체 탐지)[cite: 1]
- **Database:** MariaDB (사용자 권한 및 검사 이력 관리)[cite: 1]
- **Protocol:** TCP/IP Socket (JSON 기반 Custom Protocol)[cite: 1]
- **Hardware:** Arduino UNO (Serial 통신 기반 제어)[cite: 1]

---

## 💡 핵심 기능 및 해결 과제 (Key Features & Problem Solving)

### 1. 데이터 부족 한계 정면 돌파 (Data Strategy)[cite: 1]
- **PatchCore 도입:** 불량 데이터가 희소한 공정 특성을 고려하여, 정상 데이터만으로 학습 가능한 PatchCore 모델을 채택하여 신규 불량 대응력을 높였습니다.[cite: 1]
- **데이터 직접 구축:** YOLOv11 학습을 위해 Roboflow를 활용, 이미지 수집부터 라벨링, 증강(Augmentation)까지의 전 과정을 직접 수행하여 최적의 모델을 생성했습니다.[cite: 1]

### 2. 고성능 통합 관제 클라이언트 (MFC)[cite: 1]
- **실시간 대시보드:** 총 검사 수, 불량률, 가동률 실시간 집계 및 서버 헬스 체크(Heartbeat) 기능 구현.[cite: 1]
- **멀티스레드 안정화:** 네트워크 수신 스레드와 UI 스레드 간 자원 충돌 문제를 `CRITICAL_SECTION`과 독립 DC 관리 기법으로 해결하여 런타임 크래시를 방지했습니다.[cite: 1]

### 3. HW-SW 통합 제어 시스템[cite: 1]
- **실시간 연동:** AI 추론 결과에 따라 Python(서버)에서 아두이노로 시리얼 신호를 전달, 즉각적인 물리적 피드백(LED 및 리젝터)을 구현했습니다.[cite: 1]

---

## 🏗 시스템 아키텍처 (System Architecture)

1. **이미지 취득:** 산업용 카메라를 통한 프레임 수집.[cite: 1]
2. **AI 추론:** 학습된 모델(PatchCore/YOLO)을 통한 결함 판단.[cite: 1]
3. **결과 출력:** 판단 결과를 기반으로 하드웨어 제어 및 DB 이력 저장.[cite: 1]

---

## 🔧 설치 및 실행 방법 (Installation)
1. **Arduino:** `led_serial_json.ino` 업로드[cite: 1]
2. **Python Server:** `pip install pyserial` 후 서버 실행[cite: 1]
3. **MFC Client:** Visual Studio에서 빌드 후 실행[cite: 1]
