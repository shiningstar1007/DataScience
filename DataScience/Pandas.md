# Pandas  

python 대표 데이터 분석/처리 오픈소스 라이브러리로 필수적인 존재  
다양한 데이터에 대한 입출력, 변환, 선택, 결합, 클리닝, 그룹핑을 지원함  

설치 명령어 : $pip install pandas  

## Pandas 객체  
Pandas에서는 기본적으로 사용하는 객체는 DataFrame와 Series를 사용합니다.  
이 객체들은 빅 데이터 분석에 있어서 유용하게 사용할 수 있습니다.  

DataFrame : 테이블 데이터 객체  
- 테이블 형식으로 되어 있는 데이터를 DataFrame 라고 지칭함  
- 2차원적인 형태  

Series : 벡터 데이터 객체  
- 리스트에 가까운 형식으로 1차원적으로 나열되어 있는 형태  
- 인덱스 값이 함께 저장되며, 인덱스 값은 0부터 시작되어 저장 됨  
- dtype은 각각의 컬럼에 대한 데이터 타입  

head, tail 은 5개의 행을 보여줌, head-> 처음부터 5개, tail -> 맨 마지막에서 5개  

## DataFrame / Series dtype  
|  <center>타입</center> |  <center>설명</center> |   
|:--------:|:--------:|  
|**<center>Int64, float64</center>** | <center>64비트 정수 / 실수</center> |  
|**<center>bool</center>** | <center>True / False</center> |  
|**<center>object</center>** | <center>문자열 포함 임의의 데이터 타입</center> |  
|**<center>astype()</center>** | <center>데이터 타입 변환</center> |  
|**<center>datatime64[ns]</center>** | <center>날짜 / 시간</center> |  
|**<center>timedelta64[ns]</center>** | <center>날짜 / 시간 차이</center> |  
|**<center>pandas.to_datatime()</center>** | <center>문자를 날짜/시간으로 변환</center> |  

## NaN[Not a Number (Missing value)] : 결측값  
- "어떤 값이 존재하지 않을 때" 를 지칭  
|  <center>타입</center> |  <center>설명</center> |   
|:--------:|:--------:|  
|**<center>isnull()</center>** | <center>NaN이 있는지 여부(True/False)</center> |  
|**<center>fillna()</center>** | <center>NaN이 있는 행/열 대치</center> |  
|**<center>dropna()</center>** | <center>NaN이 있는 행/열 삭제</center> |  

# Pandas Function  
|  <center>함수</center> |  <center>설명</center> |   
|:--------:|:--------:|  
|**<center>read_csv(), write_csv()</center>** | <center>CSV 파일입출력</center> |  
|**<center>pivot_table()</center>** | <center>피봇테이블생성</center> |  
|**<center>merge(), concat()</center>** | <center>서로 다른DataFrame 결합</center> |  
|**<center>corr()</center>** | <center>상관관계계산</center> |  
|**<center>hist(), plot()</center>** | <center>데이터 히스토그램/시각화</center> |  
|**<center>dt.year/month/day/weekofyear/weekday</center>** | <center>Datetime[ns] 타입 데이터의 년/월/일/주/요일</center> |  
|**<center>resample()</center>** | <center>Datetime[ns] 타입데이터리샘플링</center> |  
