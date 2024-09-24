# VRobot_arm.ino document
## 프로젝트 개요
이 코드는 서보 모터와 아날로그 센서를 사용해 각도를 제어하고, 각도를 예측하는 시스템을 구축합니다. 5개의 서보 모터와 그에 대응하는 저항 기반 아날로그 센서를 통해 서보 모터의 현재 각도를 측정하고, 이를 시리얼 통신을 통해 입력받은 목표 각도와 비교해 서보 모터의 움직임을 제어합니다.

## 주요 기능

서보 모터 제어: 각도와 핀 번호를 입력받아 서보 모터를 해당 각도로 회전시킵니다.
캘리브레이션: 서보 모터의 0도와 180도에서의 아날로그 값을 측정하여, 아날로그 센서의 전압을 기반으로 각도를 추정합니다.
각도 예측: 아날로그 센서 값을 통해 서보 모터의 현재 각도를 추정합니다.
시리얼 통신 데이터 수신: 시리얼 통신을 통해 10개의 각도 값을 받아, 그 중 5번째에서 9번째 값에 따라 서보 모터를 제어합니다.
코드 상세 설명
1. set_servo_angle 함수
이 함수는 서보 모터의 각도를 제어하는 역할을 합니다. map 함수를 사용해 입력된 각도에 따른 펄스 폭을 계산하고, 이를 통해 서보 모터를 해당 각도로 이동시킵니다. 주기적으로 신호를 보내 50Hz 신호를 생성합니다.

2. calibration 함수
이 함수는 서보 모터의 0도와 180도에서 아날로그 센서 값을 읽어들이는 캘리브레이션 작업을 수행합니다. 이를 통해 서보 모터가 움직일 때, 아날로그 센서로부터 읽어들이는 값을 기반으로 각도를 추정할 수 있습니다. 캘리브레이션 작업 후에는 서보 모터를 다시 0도로 되돌립니다.

3. estimateAngle 함수
이 함수는 캘리브레이션된 아날로그 값을 기반으로 현재 아날로그 입력값을 각도로 변환하는 역할을 합니다. 0도와 180도에서의 아날로그 값을 이용해, 선형 관계를 통해 각도를 추정합니다.

4. get_data 함수
이 함수는 시리얼 통신을 통해 10개의 각도 값을 받아오고, 입력이 유효한지 확인합니다. 입력된 데이터가 9개의 콤마로 구분된 10개의 값인지 확인한 후, 이 값을 배열에 저장합니다. 이를 통해 서보 모터의 움직임을 제어하는 데이터를 받아옵니다.

5. setup 함수
setup 함수에서는 시리얼 통신을 초기화하고, 서보 모터 핀들을 출력 모드로 설정합니다. 또한, 캘리브레이션 작업을 통해 서보 모터의 0도와 180도에서 아날로그 센서의 값을 미리 측정해 저장합니다.

6. loop 함수
loop 함수에서는 주기적으로 시리얼 통신을 통해 받은 각도 데이터를 기반으로 서보 모터를 제어합니다. 각 서보 모터는 시리얼로 입력받은 값에 따라 각도를 설정하며, 주기적으로 현재 각도를 측정하여 시리얼 모니터에 출력합니다. 특히, 1번, 3번, 5번 서보 모터의 경우 아날로그 입력을 통해 현재 각도를 추정하여 출력합니다.