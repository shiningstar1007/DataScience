# NumPy (Numerical Python)

- Python 대표 선형대수 라이브러리
- 고성능의 벡터/메트릭스 연산 및 바이너리 데이터 타입을 지원함
- 수치 해석을 할 때 많이 사용 됨
- NumPy 기본적인 데이터 타입/객체는 ndarray(or array) : NumPy 기본 객체, n-차원 배열

설치 명령어 : $pip install numpy

numpy를 사용방법 : import numpy as np
- 기본적으로 numpy의 줄인 np로 선언해서 사용함

## ndarray 다차원 배열 객체
ndarray는 같은 종류의 데이터를 담을 수 있는 포괄적인 다차원 배열로
모든 데이터는 같은 자료형이어야 함

## NumPy 기본적인 데이터 타입/객체
|  <center>타입</center> |  <center>설명</center> |   
|:--------:|:--------:|  
|**<center>ndarray.ndim</center>** | <center>차원개수(예, 2)</center> |  
|**<center>ndarray.size</center>** | <center>배열의원소개수(예, 15)</center> |  
|**<center>ndarray.shape</center>** | <center>배열크기(예, 3x5 메트릭스: (3, 5))</center> |  
|**<center>ndarray.itemsize</center>** | <center>원소의바이트크기(예: 8 byte)</center> |  
|**<center>ndarray.dtype</center>** | <center>배열의데이터타입(예: np.int64)</center> |  
|**<center>ndarray.data</center>** | <center>배열의데이터</center> |  

## NumPy 기본적인 함수
|  <center>함수</center> |  <center>설명</center> |   
|:--------:|:--------:|  
|**<center>sqrt</center>** | <center>배열 원소의 제곱근 계산</center> |  
|**<center>square</center>** | <center>배열 원소의 제곱값 계산</center> |  
|**<center>abs</center>** | <center>배열 원소의 절대값 계산</center> |  
|**<center>sin</center>** | <center>배열 원소의 부호를 계산</center> |  
|**<center>ceil</center>** | <center>배열 원소의 소수자리 올림</center> |  
|**<center>floor</center>** | <center>배열 원소의 소수자리 버림</center> |  
|**<center>rint</center>** | <center>배열 원소의 소수자리 반올림. dtype 유지 </center> |  
|**<center>modf</center>** | <center>배열 원소의 몫과 나머지를 각각 배열로 반환</center> |  
|**<center>isnan</center>** | <center>배열 원소가 숫자인지 아닌지 NaN 나타내는 boolean 배열</center> |  
|**<center>cos</center>** | <center>배열 원소의 삼각함수 값을 계산</center> |  
|**<center>mean</center>** | <center>배열 원소의 평균값 계산</center> |  
|**<center>median</center>** | <center>배열 원소의 중앙값 계산</center> |  
|**<center>var</center>** | <center>배열 원소의 분산 계산</center> |  
|**<center>std</center>** | <center>배열 원소의 표준편차 계산</center> |  
|**<center>exp</center>** | <center>배열 원소의 성분을 무리수 e의 지수로 삼은 값 계산</center> |  
|**<center>Log, log10, log2, log1p</center>** | <center>배열 원소의 자연로그, 로그10, 로그2, 로그(1+x) 계산</center> |  
|**<center>expm1</center>** | <center>log1p()로 변환 된 값을 원래 값으로 변환</center> |  
|**<center>reshape</center>** | <center>현재 배열의 차원을 변경하여 행렬을 반환</center> |  
|**<center>corrcoef</center>** | <center>피어슨 상관계수를 계산</center> |  
|**<center>concatenate</center>** | <center>배열을 하나로 합칠 때</center> |  
|**<center>vstack</center>** | <center>배열을 세로로 합칠 때</center> |  
|**<center>hstack</center>** | <center>배열을 가로로 합칠 때</center> |  
|**<center>random</center>** | <center>난수 생성</center> |  
