# BulbPredictionDataVisualization

### Description

2020년 2학기 '데이터 시각화' 수업에서 진행한 프로젝트로 만든 'flexdashboard' 기반의 반응형 웹사이트이다. 사용된 데이터는 국내 자동차 부품 회사인 'SL'의 전구 표면 헤드라이트 실측데이터를 사용하였다. 이를 기반으로 'h20' 패키지를 사용하여 딥러닝 모델을 학습시켰고, 주어진 변수를 기반으로 새롭게 만들어질 헤드라이트의 표면온도와 주변온도가 어떻게 될지 예측하고 새로운 데이터를 뽑아낸다. 


이번 프로젝트의 목표는 두가지이다. 첫번째는 도메인 지식은 있으나 데이터 분석과 모델링에 대해서는 문외한인 실무진들과 운영진들에게 학습한 딥러닝 모델의 성능에 대하여 효과적으로 보고하는 것이다. 이것은 모든 데이터 시각화의 공통된 목표일 것이다. 아무리 유의미한 데이터를 추출하였다고 하더라도, 데이터에 대한 지식이 없는 일반인이 'raw data'를 이해하는 것은 굉장히 어려운 일이고, 이를 효과적으로 전달하는 것은 데이터 사이언스의 최종단계이다. 우리는 이에 대한 인식을 분명히하고, 어떻게 하면 최적화된 딥러닝에 성능에 대해서 증명할 수 있을지 클라이언트와 소통하여 니즈를 충족시키고자 하였다. 먼저 모델별로 각 변수에 의한 실측온도와 예측온도의 상관관계를 보여줄 수 있도록 '모델링별 변수간 상관관계' 페이지를 구성하였다. 그리고 분석모델의 성능을 한눈에 비교할 수 있도록 RMSE 값과 그래프를 배치하고, 모델별 실측온도와 예측온도간의 오차에 등급을 매기고 파이그래프로 표현하였다. 실측온도와 모델별 예측온도를 3D 전구모양으로 표현하는 것으로 딥러닝 최적화 모델이 다른 기본 모델에 비해 월등한 성능을 보이는 것을 증명하였다.


프로젝트의 두번째 목표는 이후 딥러닝을 활용한 예측과정을 간소화시키는 것이었다. 딥러닝 모델은 R의 'h2o' 패키지를 이용하여 최적화 과정을 거쳤는데, 이를 'R tools'를 이용해서 다루기에는 실무진 입장에서 굉장히 번거로운 일이 된다. 최적화 모델을 구성하는데 성공했지만 이를 사용하는 것이 어려워 사용성이 떨어지는 현상이 발생하는 것이다. 따라서 우리는 실무진이 이용하기에 간편한 엑셀(.csv) 파일과 웹을 이용하는 것만으로도 새로운 예측이 가능할 수 있도록 편의성을 제공하는 것을 목표로 하였다. 구현한 웹페이지의 '5. New Data, New Predict'는 그 결과물이다. 웹페이지에서 'Browse'를 통해 로컬 드라이브에 존재하는 csv 파일을 업로드하는 것이 가능하다. csv 파일이 업로드 되면 서버에 저장된 딥러닝 모델을 통해 새로운 분석을 수행한다. 분석이 완료되면 예측한 온도데이터를 가지고 3D 그래프를 구현함과 동시에, csv 테이블을 그래프 우측에 출력한다. 예측한 온도 변수를 가지고 있는 테이블을 csv 파일로 내려받는 것 또한 테이블 좌측 상단의 다운로드 버튼을 클릭하는 것으로 간편하게 실행된다.


우리는 웹페이지를 구성하기 위해서 'flexdashbard'를 사용하였다. flexdashbard는 R markdown을 사용하기 때문에, R shiny보다 비교적 사용하기 간편하여 대쉬보드를 구성하는데 있어서 수월하다는 장점이 있다. 또한 딥러닝을 위해서 사용했던 데이터를 모두 사용한다면, 변수가 혼재되어있고 업로드 및 그래프 구성 시간이 매우 오래걸리기 때문에 데이터를 선별하여 사용했다. 우리는 먼저 클라이언트에게 받았던 실측온도 데이터(엑셀파일) 중 하나를 랜덤 선별하였고, 3D 그래프를 표현하기 위해서 추출된 데이터를 계통추출법을 사용하여 4의 배수마다 데이터 값을 한번 더 추출하는 방식을 택했다. 3D 데이터를 표현하는데 있어서 더 긴 로딩이 필요하기 때문에, 이를 조금이라도 줄이기 위한 방법이었다. 데이터 시각화는 ggplot2 패키지와 plotly 패키지를 사용하여 표현하였다. 


*** 업러드한 R markdown에는 h20 최적화 모델과 데이터를 제외하고 업로드하였다. 이는 'SL' 회사와의 산업연계로 진행된 프로젝트였기 때문에 이를 제외하기로 결정하였다.

### Site

https://patience94.shinyapps.io/BulbPredictionProject/


### Detail

#### 1. 프로젝트 개요
![프로젝트개요](https://user-images.githubusercontent.com/55008408/116419569-27128880-a878-11eb-9352-65b9bf595994.gif)

<br> 프로젝트에 대한 전체적인 개요를 설명해주는 페이지다. 프로젝트의 목적과 데이터 설명, 변수 예시 등이 기록되어 있다.

<br>
<br>

#### 2. 데이터 변수 소개
![데이터변수소개](https://user-images.githubusercontent.com/55008408/116419659-3d204900-a878-11eb-8af1-d411967c435b.gif)

<br> 변수에 대한 소개를 목적으로하는 페이지이다. 딥러닝 최적화를 위해서 사용되었던 변수의 갯수는 훨씬 더 많으나, shiny 서버의 로딩 시간과 그래프 구성 시간 등을 고려하여 페이지 구성시엔 제한적으로 사용하였다. 변수 소개 페이지의 로딩 시간을 최소화하기 위해서 img 파일을 붙이는 방식으로 진행하였다.

<br>
<br>

#### 3. 모델링별 변수간 상관관계
![모델링별 변수간 상관관계](https://user-images.githubusercontent.com/55008408/116420131-aacc7500-a878-11eb-81a5-3d42edaac399.gif)

<br> 여기부터는 반응형 웹으로 작업되었다. 각 변수를 조정했을 때 회귀분석, h2o 기본 모델, h2o 최적화 모델에서의 실측온도와 예측온도 간의 상관관계를 그래프를 통해서 나타냈다. 보다시피 최적화 모델에서 가장 높은 상관관계를 가지는 것을 알 수 있다.

<br>
<br>

#### 4. 모델링 성능 비교 및 3D 
![모델링 성능 비교 및 3D](https://user-images.githubusercontent.com/55008408/116421132-891fbd80-a879-11eb-9d65-9bcee9c0682a.gif)

<br> RMSE 값을 한눈에 비교할 수 있게끔 모델별 그래프와 수치를 나타냈다. 이후 실측 온도와 예측 온도 간의 차이를 5% 이내, 10% 이내, 10% 이상으로 구분하여 A, B, C 등급을 메기고, 각 rate의 수를 파이 그래프로 나타냈다. 마지막으로 실측온도를 3D 전구 그래프로 표현하고, 이를 모델별 예측온도와 비교할 수 있도록 하였다. 각 모델에 맞는 radio 버튼을 클릭하면, 각 모델로 예측한 온도를 띄우고 있는 3D 그래프가 나타나게 된다.

<br>
<br>

#### 5. New Data, New Predict
![New Data, New Predict](https://user-images.githubusercontent.com/55008408/116422519-c9cc0680-a87a-11eb-9bec-9ad115941a6e.gif)

<br> Browse를 클릭하여, 변수가 매칭된 csv 파일을 입력하면 값에 맞춘 딥러닝 예측과 함께, 새로운 데이터의 시각화를 진행한다. 또한 새롭게 생성된 데이터는 3D 그래프 옆에 테이블을 통해서 가시적으로 표현되어 직접 확인가능하다.

<br>

![데이터 다운로드](https://user-images.githubusercontent.com/55008408/116422860-1f081800-a87b-11eb-9ebb-93d8e80e5ac9.gif)

<br> 새롭게 생성된 데이터는 테이블 좌측 상단의 아이콘을 통해서 간편하게 다운로드가 가능하다. 이때 이름엔 현재 날짜와 'update'라는 문구가 추가되어 다운로드 되도록 되어 있다. 사용자는 이를 통해 새롭게 예측된 데이터를 손쉽게 확보할 수 있다. 

