# 📈 BigsCoin  
안녕하세요! 제 14회 투빅스 컨퍼런스 프로젝트 **Bigscoin**입니다.    

**Bigscoin**은 사용자들에게 설명 가능한 개인 맞춤형 비트코인 패턴 알림과 예측 서비스를 제공합니다.  

기존에 블랙박스로 불리던 AI모델의 예측 결과에 설명성과 신뢰성을 더해주기 위해  

다양한 XAI 기법을 활용하여 비트코인 차트의 패턴과 종가 예측 결과를 한 눈에 알아볼 수 있는 시스템을 개발했습니다.  


[![youtube](https://img.shields.io/badge/Youtube-Link-red)]
[![googledrive](https://img.shields.io/badge/report-Link-lightgrey)]
<br>  

**14th Tobig's TimeSeries and Explainable AI Conference**  

Team name: **Bigscoin**  

Project: **Explainable Bitcoin Pattern Alert and Forecasting Service**   

<p align="center"><img src="https://user-images.githubusercontent.com/72960666/179309070-5bd34ff4-0d45-4dca-89d3-207c59c07161.png"></p>


## Classification
코인 투자자들은 시각적으로 보여지는 차트의 패턴을 참고하여 투자 전략을 세우는 경우가 많습니다. 

그 중 코인차트에서 가장 많이 관측되는 패턴 5가지는 다음과 같습니다.
<p align="center"><img src="https://user-images.githubusercontent.com/72960666/179292406-5e47a37c-cb4c-41a5-894f-b15d8ddb5e5d.png"></p>

하지만, **패턴이 나타날 때까지 모니터링을 하는 것은 굉장한 노동력과 시간이 소모되는 행위**입니다.  
또한 기존의 차트 패턴 감지 서비스들은 한 눈에 알아보기 어렵고,  
설명력이 누락된 경우가 많아 결과를 신뢰하기 어렵습니다.  

이러한 불편함을 해결하기 위해 저희는 **설명 가능한 딥러닝 모델**을 활용하여  
**실시간 패턴 알림 서비스**를 기획하게 되었습니다.  

### Data   
- pyupbit 패키지 활용하여 5분봉 차트의 시가, 고가, 저가, 종가 크롤링 [2017년 8월 ~ 2022년 5월]  
- mpl_finance 패키지를 통한 캔들스틱 이미지 변환 (model input)  
- 5가지 패턴 종류에 대한 레이블링

### Model  
저희는 **Conv2d 기반 모델** 출력을 가시적으로 해석하기 위해 **Gradcam**을 활용했습니다.  
모델이 어느 부분을 보고 해당 레이블로 예측을 하게 되었는지 알 수 있기에   
사용자는 모델이 예측한 패턴이 유의미한 결과인지 쉽게 분석하고, **패턴의 신뢰 여부를 결정**할 수 있습니다.  

### Web 
<p align="center"><img src="https://user-images.githubusercontent.com/72960666/179319379-4b9be555-b059-49f2-9a0d-884b5e462401.png"></p>
<p align="center"><img src="https://user-images.githubusercontent.com/72960666/179319381-31e7d716-de2b-43ad-ba0b-85f7dceb89d5.png"></p>

## Regression
패턴 알림을 받은 사용자는 투자 전략에 대해 고민하게 됩니다.  
특히 향후 상승 및 하락을 예측할 수 없는 **triangle 패턴**의 경우,  
저희 서비스의 **설명 가능한 시계열 예측 모델**을 통해 상승 및 하락 여부를  
보조지표로서 제공해 줌으로써 추가적인 투자 전략 수립에 도움을 줄 수 있습니다.  

### Data   
- pyupbit 패키지를 활용하여 5분봉 차트의 시가, 고가, 저가, 종가 크롤링 [KRW-BTC 단일종목 학습]  
- 종가 예측을 위한 sliding window 형태의 data loader 생성  

### Model  
**Trend 및 Seasonality로 분해**하여 예측의 설명성을 제공하는 딥러닝 아키텍처인 **Nbeats 모델**을 활용했습니다.  
**Drop-out**을 추가하여 예측할 때마다 랜덤한 예측값을 반환하기 때문에  
예측 표본에 대한 통계적인 추정이 가능하고, 모델을 신뢰할 수 있습니다.  

### Web  
<p align="center"><img src = "https://user-images.githubusercontent.com/72960666/179319371-873b11e9-87bf-4cd2-88eb-654994356918.png"></p>


## Contributor 🧑‍🤝‍🧑

- 본 프로젝트에는 [빅데이터 분석 및 인공지능 대표 연합동아리 ToBig's](http://www.datamarket.kr/xe/) 멤버들이 참여하였습니다.

|기수|이름|팀|역할|
|:-----:|:-----:|:-----:|:-----:|
|16기|[김권호](https://github.com/kkhv)|웹 서빙|Project Leader,  Backend|
|16기|[박한나](https://github.com/hanna56)|웹 서빙|Frontend|
|16기|[김윤혜](https://github.com/yoonene)|웹 서빙|Backend|
|16기|[이예림](https://github.com/YerimLee00)|분류|Modeling,  Grad-CAM Visualization,  Presentation|
|17기|[나세연](https://github.com/seyeonrha)|분류|Experiments|
|17기|[유현우](https://github.com/yhw4343)|분류|Data Inspection(데이터 검수)|
|16기|[김주호](https://github.com/Jooho-Git)|회귀|Probabilistic Modeling,  Nbeats Visualization,  Experiments|
|17기|[김현태](https://github.com/hyuntai97)|회귀|DeepAR, Nbeats, Informer Modeling,  Experiments|
|17기|[김상윤](https://github.com/tkddbs0411)|회귀|ARIMA Modeling,  DeepAR Tuning|

