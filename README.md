# Bigscoin 

Bigscoin은 사용자들에게 설명 가능한 맞춤 비트코인 패턴 알림과 예측 서비스를 제공합니다. 예측 결과에 신뢰성을 더해주기 위해 다양한 XAI 기법을 활용하여 이를 시각적으로 확인할 수 있는 시스템을 개발했습니다. 

## Classification - Main Service 
코인 투자자들은 시각적으로 보여지는 차트를 참고하여 투자 전략을 세우는 경우가 많습니다. 

그 중 코인차트에서 가장 많이 관측되는 패턴 5가지 
- 코인 차트 5가지 그림 

하지만, 패턴이 나타날 때까지 모니터링을 하는 것은 굉장한 노동력 + 시간소모적인 행위입니다. 이를 해결하기 위해 딥러닝 모델을 활용한 실시간 패턴 예측, 알람 서비스를 기획하게 되었습니다.  

### Model 
- data prepare
1) pyupbit 패키지 활용 차트 5분봉 ohlcv 크롤링 [2017년 8월 ~ 2022년 5월]  
2) mpl_finace 패키지를 통한 캔들스틱 이미지 변환 (model input)  
3) 일정 시간 간격으로 sliding 하며 패턴 종류 추출 레이블링 작업.

- model train 
model 아키텍쳐 그림. (conv2d - maxpool2d - ... - dense layer - softmax)

- XAI 
gradcam: CNN 기반 모델 출력을 가시적으로 해석하기 위한 방법론. 
모델이 어느 부분을 보고 해당 레이블로 예측을 하게 되었는지 설명 가능. 
이를 통해 패턴 알람을 받은 사용자는 모델이 예측한 패턴이 유의미한 결과인지 쉽게 분석하고 패턴 신뢰 여부를 결정할 수 있다.  

gradcam 시각화 결과 그림. 

- 최종 서빙 형태 

서빙 이미지 결과 그림. 


## Regression - Sub Service 
알람을 통해 패턴 발생을 인지한 사용자는 투자 전략에 대한 고민을 하게된다. 이 때, 딥러닝 모델이 예측한 상승 하락 여부를 보조지표로 제공해 줌으로써 추가적인 계획 수립에 도움을 줄 수 있다. 

- data prepare
1) pyupbit 패키지를 활용 차트 5분봉 ohlcv 크롤링 [KRW-BTC 한 종목만 학습]
2) close (종가) 예측을 위한 sliding window 형태의 data loader 생성 

- model train (Nbeats)
model 아키텍쳐 그림. 혹은 sliding window 그림? 

- XAI 
Nbeats model output 그림. 
forecasting의 결과와 더불어 이를 설명할 수 있는 추가적인 보조 자료를 얻을 수 있는 Nbeats 모델. 예측결과를 Seasonality와 Trend의 합으로 표현할 수 있기 때문에 이를 분해하여 사용자에게 시각적인 자료를 제공할 수 있다. 

- 최종 서빙 형태 

서빙 이미지 결과 그림. 





