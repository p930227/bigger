# 본인의 과제명 작성

학과 | 학번 | 성명
---- | ---- | ---- 
통계학과 | 201646114 |박준형


## 프로젝트 개요
부산항 물동량(Container)를 이용한 2019년도 2분기 경제성장률(GDP) 예측

목적  
1. 1분기보다 2분기 경제성장률이 좋았던 적이 존재하는가?
2. 정부의 발표대로 2019년도 2분기 경제성장률이 1.5%의 도달할 수 있을것인가?

개요
1. Container, GDP, Container & GDP, Time_Series Data 파일생성 : 각각의 파일을 만들고 Main 파일에서 import하여 사용.
2. 각각의 Data에 대해 필요한 역할을 하는 함수를 각 파일내에 생성 : Main 파일에서 import하여 함수호출.
3. 전체 Container, GDP를 보여주거나 개별 년도_분기별 Container, GDP를 보여줄 수 있도록 함수 생성.
4. 위의 3에대한 시각화 & 목적 1 확인
5. 시계열(Time_Series) 분석을 위해 새롭게 데이터전처리 (index, columns 조정)
6. Container Data를 GDP Data에 적합
7. 2019년도 2분기 GDP 예측 및 시각화 - 예측 값 및 유의수준 a=0.05(95% C.I)에서 상한과 하한값 도출(목적 2 확인)
8. '경제대공황(서브프라임모기지)'이 일어났던 2008년도의 Data를 이상치로 판단하여 제거 후 재적합 후 위의 7번 수행

결과
1. 목적 1 물음에 대해 2006년 ~ 2019년의 13년동안 3번 존재.
2. 목적 2 물음에 유의수준 a=0.05(95% C.I)에서 예측 값 0.35%, 상한 및 하한(1.02%, -0.28%). 즉 도달 못함
3. 사실, GDP예측에는 Container Data뿐만아니라 달러환율, 위안환율, 유가, 국제정세등 많은 변수를 필요로 한다. 따라서 정확한 예측이라 할 수 없다.


## 사용한 공공데이터 
[데이터보기](https://github.com/cybermin/python2019/blob/master/%EB%B6%80%EC%82%B0%EA%B5%90%ED%86%B5%EA%B3%B5%EC%82%AC_%EB%8F%84%EC%8B%9C%EC%B2%A0%EB%8F%84%EC%97%AD%EC%82%AC%EC%A0%95%EB%B3%B4_20190520.csv)

## 소스
* [링크로 소스 내용 보기](https://github.com/cybermin/python2019/blob/master/tes.py) 

* 코드 삽입
~~~python
items = list(range(1,11))

for i in items:
    print(i)
~~~
