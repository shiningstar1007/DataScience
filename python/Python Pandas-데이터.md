# Python Pandas-데이터

## 데이터프레임 구조 확인하기  
### 데이터 내용 확인  
- 데이터 앞부분 내용 확인 : DataFrame객체.head(n)  
- 데이터 뒷부분 내용 확인 : DataFrame객체.tail(n)  
- n값 미 입력시 default 값은 5  
- n값 입력 시 입력한 값만큼 출력 데이터 출력  

### 데이터 요약 정보 확인  
#### 데이터프레임의 크기(행,열) : DataFrame객체.shape  
- 행의 개수와 열의 개수를 tuple형태로 반환함  

#### 데이터프레임의 기본 정보 : DataFrame객체.info()  
- 데이터프레임 구조, index 개수, columns 개수와 결측값, 데이터 타입, 메모리 사용량 출력  

#### 데이터프레임의 자료형 확인 : DataFrame객체.dtypes  
- 데이터프레임 객체의 자료형을 출력  

#### 데이터프레임의 특정 column의 자료형 확인 : DataFrame객체.colunm명.dtypes  
- 데이터프레임 객체의 특정 column의 자료형을 출력   

#### 데이터프레임의 기술 통계 정보 요약 : DataFrame객체.describe()  
- 데이터프레임 내 수치형 데이터의 통계 정보를 출력  
- 기본적으로 count, mean, std, min, 25%, 50%, 75%, max 정보가 출력  
- unique(고유값), top(최빈값), freq(빈도수) 까지 출력하고 싶은 경우엔 DataFrame객체.describe(include='all')  


### 데이터 개수 확인하기  
- 각 열의 데이터 개수 확인 : DataFrame객체.count()  
- 각 열의 고유값 개수 확인 : DataFrame객체["Column 이름"].value_counts()  
- 출력 시 데이터 타입은 Series 로 반환됨  

## 통계 함수 적용  
### 평균값  
- 모든 열의 평균값 확인 : DataFrame객체.mean()  
- 특정 열의 평균값 확인 : DataFrame객체["Column 이름"].mean()  

### 중간값  
- 모든 열의 중간값 확인 : DataFrame객체.median()  
- 특정 열의 중간값 확인 : DataFrame객체["Column 이름"].median()  

### 최대값  
- 모든 열의 최대값 확인 : DataFrame객체.max()  
- 특정 열의 최대값 확인 : DataFrame객체["Column 이름"].max()  

### 최소값  
- 모든 열의 최소값 확인 : DataFrame객체.min()  
- 특정 열의 최소값 확인 : DataFrame객체["Column 이름"].min()  

### 표준편차  
- 모든 열의 표준편차 확인 : DataFrame객체.std()  
- 특정 열의 표준편차 확인 : DataFrame객체["Column 이름"].std()  

### 상관계수  
- 모든 열의 상관계수 확인 : DataFrame객체.corr()  
- 특정 열의 상관계수 확인 : DataFrame객체["Column 이름","Column 이름"].corr()  

## Pandas 내장 그래프 도구  
- 선 그래프 : DataFrame객체.plot()  
- 막대 그래프 : DataFrame객체.plot(kind='bar')  
- 히스토그램 : DataFrame객체.plot(kind='hist')  
- 산점도 : DataFrame객체.plot(x=데이터, y=데이터, kind='scatter')  
- 박스 플롯 : DataFrame객체.plot(kind='box')  