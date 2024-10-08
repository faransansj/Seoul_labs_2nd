# 2024 MCU 경진대회 예선
Goal : 비데를 설계하고 기능을 구현하시오  

### 주요 기능 
1) 컨트롤러 : 스위치를 눌러서 각종기능 제어 + LED 인디케이터 + 부저를 통해 경고음 재생
2) 온열시트 : 사용자가 원하는 온도로 조절
3) 수위센서 : 물이 정상적으로 공급되는지 확인 
4) 근접센서 : 동작인식 센서를 이용해서 사용자가 가까이 오면 변기가 열림
5) 자동개패 : 서보모터를 이용해 변기커버의 움직임 구현
6) 노즐모터 : 스탭모터 이용해서
- 부가기능   
+ 거리센서를 양쪽에 부착해서 사용자가 정상적으로 안착하는지 구현
+ 장기간 변기에 앉아 있으면 경고음 재생

### 구현 계획
- 컨트롤러
74HC595 이용해서 LED 제어 [참고자료](https://m.blog.naver.com/dmaker123/221894002813)  
74HC165 이용해서 switch 입력 받음 [참고자료](https://kocoafab.cc/tutorial/view/503)
8개 디지털 핀 필요

수동 부저를 통해 각종 알림음 재생  
이때 라이브러리를 따로 하나 만들어서 각 상황에 따른 알림음 사전에 작성한다.  
1개 디지털 핀 필요    
  
- 온열시트
릴레이 모듈을 이용해서 가열부에 전원을 공급한다.
LM35 온도센서를 이용해서 온도 모니터링
1개 디지털 핀 필요

- 수위센서
수위센서를 이용해서 물의 높이에 따른 저항값을 읽어들인다.
1개 아날로그 핀 필요

- 근접센서

- 자동개패
  
---
## HardWare

## SoftWare
```C++
do something...
```
