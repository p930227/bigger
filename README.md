# 2019년 2분기 경제성장률(GDP) 예측

학과 | 학번 | 성명
---- | ---- | ---- 
통계학과 | 201646114 |박준형


## 프로젝트 개요
* 부산항 물동량(Container)를 이용한 2019년도 2분기 경제성장률(GDP) 예측

* 목적  
1. 1분기보다 2분기 경제성장률이 좋았던 적이 존재하는가?
2. 정부의 발표대로 2019년도 2분기 경제성장률이 1.5%의 도달할 수 있을것인가?

* 개요
1. Container, GDP, Container & GDP, Time_Series Data 파일생성 : 각각의 파일을 만들고 Main 파일에서 import하여 사용.
2. 각각의 Data에 대해 필요한 역할을 하는 함수를 각 파일내에 생성 : Main 파일에서 import하여 함수 호출.
3. 전체 Container, GDP를 보여주거나 개별 년도/분기별 Container, GDP를 보여줄 수 있도록 함수 생성.
4. 위의 3에대한 시각화 & 목적 1 확인
5. 시계열(Time_Series) 분석을 위해 새롭게 데이터전처리 (index, columns 조정)
6. Container Data를 GDP Data에 분기별 적합
7. 2019년도 2분기 GDP 예측 및 시각화 - 예측 값 및 유의수준 a=0.05(95% C.I)에서 상한과 하한값 도출(목적 2 확인)
8. '경제대공황(subprime mortgage)'이 일어났던 2008년도의 Data를 이상치로 판단하여 제거 후 재적합 후 위의 7번 수행

* 결과
1. 목적 1 물음에 대해 2006년 ~ 2019년의 13년동안 3번 존재.
2. 목적 2 물음에 유의수준 a=0.05(95% C.I)에서 예측 값 0.35%, 상한 및 하한(1.02%, -0.28%). 즉 도달 못함
3. 사실, GDP예측에는 Container Data뿐만아니라 달러환율, 위안환율, 유가, 국제정세등 많은 변수를 필요로 한다. 따라서 정확한 예측이라 할 수 없다.


## 사용한 공공데이터 
[데이터보기](https://new.portmis.go.kr/portmis/websquare/websquare.jsp?w2xPath=/portmis/w2/main/index.xml&page=/portmis/w2/cm/sys/UI-PM-MT-001-021.xml&menuId=0045&menuCd=M4735&menuNm=사이트맵)

## 소스
* Main 파일만 삽입하였고, 나머지 전체 Code파일은 첨부하였습니다.
~~~python
"""
부산대학교 통계학과 4학년 박준형
분기별 부산항 물동량(Container) Data를 이용한 2019년도 2분기 경제성장률(GDP) 예측
"""

import GDP_Ft as GF
import Container_Ft as CF
import GDP_Container_Ft as GCF
import time_series as TS
from fbprophet import Prophet


##### GDP 확인 #####
GDP_All=input("2006_1분기부터 2019_1분기까지의 GDP를 확인하시겠습니까 (Y/N) ?").upper()
GF.GDP_All(GDP_All)
GDP_Y_Q=input("특정 년도/분기의 GDP를 확인하시겠습니까 (Y/N) ?").upper()
GF.GDP_Y_Q(GDP_Y_Q)


##### Container 확인 #####
Container_All=input("2006_1분기부터 2019_1분기까지의 Container를 확인하시겠습니까 (Y/N) ?").upper()
CF.Container_All(Container_All)
Container_Y_Q=input("특정 년도/분기의 Container를 확인하시겠습니까 (Y/N) ?").upper()
CF.Container_Y_Q(Container_Y_Q)


##### GDP & Container #####
Plot_Confrim = input("1분기보다 2분기의 경제성장률이 좋았던 적이 있는지 그래프로 확인하시겠습니까 (Y/N) ?").upper()
GCF.Data_Plot(Plot_Confrim)


##### Time Series 전체 기간 #####
# Value & Graphic
TS_Confrim = input("Time_Series 모델로 적합한 적합 모델의 Time_Series 그래프와 2019년도 2분기 예측값을 확인하시겠습니까 (Y/N) ?").upper()
if TS_Confrim == 'Y' :
    Predict_GDP = TS.All_Time(TS_Confrim)    
    m=Prophet()
    m.fit(Predict_GDP)
    future = m.make_future_dataframe(periods=31)
    forecast = m.predict(future)
    m.plot(forecast)


##### Time Series - 2008(경제대공황)년도 삭제 후 #####
# Value & Graphic
TS_Confrim = input("2008년(경제대공황)을 제외하고 적합한 적합 모델의 Time_Series 그래프와 2019년도 2분기 예측값을 확인하시겠습니까 (Y/N) ?").upper()
if TS_Confrim == 'Y' :
    Predict_GDP = TS.Del_Time(TS_Confrim)    
    m=Prophet()
    m.fit(Predict_GDP)
    future = m.make_future_dataframe(periods=31)
    forecast = m.predict(future)
    m.plot(forecast)
~~~
