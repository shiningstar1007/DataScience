# Python Pandas-연산

## 산술 연산  
### 시리즈(series) 연산  
- 시리즈 객체와 숫자 연산  

```python
import pandas as pd

dictionry_Data = pd.Series({'사과' : 1000, '배' : 2000, '바나나' : 3000})
averageData = dictionry_Data / 100
print(averageData) 

Output
사과     10.0
배      20.0
바나나    30.0
dtype: float64
```
- 시리즈와 시리즈를 연산  

```python
import pandas as pd

dictionry_Data1 = pd.Series({'사과' : 1000, '배' : 2000, '바나나' : 3000})
dictionry_Data2 = pd.Series({'배' : 30, '바나나' : 20, '사과' : 10})

addValue = dictionry_Data1 + dictionry_Data2
minusValue = dictionry_Data1 - dictionry_Data2
multipValue = dictionry_Data1 * dictionry_Data2
divisionValue = dictionry_Data1 / dictionry_Data2

print(addValue)
print(minusValue)
print(multipValue)
print(divisionValue)
print(type(divisionValue))

Output
바나나    3020
배      2030
사과     1010
dtype: int64
바나나    2980
배      1970
사과      990
dtype: int64
바나나    60000
배      60000
사과     10000
dtype: int64
바나나    150.000000
배       66.666667
사과     100.000000
dtype: float64
<class 'pandas.core.series.Series'>

# 연산 결과를 데이터 프레임으로 합치기  
result = pd.DataFrame([addValue, minusValue, multipValue, divisionValue],
                      index=['더하기', '빼기', '곱하기', '나누기'])
print(result)

Output
         바나나             배       사과
더하기   3020.0   2030.000000   1010.0
빼기    2980.0   1970.000000    990.0
곱하기  60000.0  60000.000000  10000.0
나누기    150.0     66.666667    100.0
```
- 시리즈 값 중에 NaN이 있는 경우  

```python
import pandas as pd
import numpy as np

dictionry_Data1 = pd.Series({'사과' : 1000, '배' : 2000, '바나나' : 3000})
dictionry_Data2 = pd.Series({'귤' : 30, '바나나' : 20, '사과' : np.nan})

addValue = dictionry_Data1 + dictionry_Data2
print(addValue)

Output
귤         NaN     # Data1에 귤이 없기 때문에 더할 수 없어서 NaN 
바나나    3020.0  # Data1과 Data2에 바나나 값이 있기 때문에 더하기
배         NaN     # Data2에 배가 없기 때문에 더할 수 없어서 NaN 
사과        NaN   # Data2에 사과 값이 NaN이기 때문에 더할 수 없어서 NaN
dtype: float64
```

## 연산 메소드  
- fill_value는 NaN인 경우 NaN 대신 넣을 값을 지정  
- 시리즈(Series)객체1.add(시리즈(Series)객체2, fill_value=0) #더하기  
- 시리즈(Series)객체1.sub(시리즈(Series)객체2, fill_value=0) #빼기  
- 시리즈(Series)객체1.mul(시리즈(Series)객체2, fill_value=0) #곱하기  
- 시리즈(Series)객체1.div(시리즈(Series)객체2, fill_value=0) #나누기  

```python
import pandas as pd
import numpy as np

dictionry_Data1 = pd.Series({'사과' : 1000, '배' : 2000, '바나나' : np.nan})
dictionry_Data2 = pd.Series({'배' : 30, '바나나' : 20 , '사과' : 10})

addValue = dictionry_Data1.add(dictionry_Data2, fill_value=0)
minusValue = dictionry_Data1.sub(dictionry_Data2, fill_value=0)
multipValue = dictionry_Data1.mul(dictionry_Data2, fill_value=0)
divisionValue = dictionry_Data1.div(dictionry_Data2, fill_value=0)

print(addValue)
print(minusValue)
print(multipValue)
print(divisionValue)
print(type(divisionValue))

Output
바나나      20.0 # Data1의 바나나 값이 NaN이기 때문에 0으로 변환 후 연산
배      2030.0
사과     1010.0
dtype: float64
바나나     -20.0 
배      1970.0
사과      990.0
dtype: float64
바나나        0.0 
배      60000.0
사과     10000.0
dtype: float64
바나나      0.000000
배       66.666667
사과     100.000000
dtype: float64
<class 'pandas.core.series.Series'>
```

## 데이터프레임 연산  
- 데이터프레임(DataFrame) 객체와 숫자 연산  

```python
import pandas as pd

dictionry_Data = {'이름':['사과','배','딸기','바나나'],
                  '가격':[1000,2000,3000,1500],
                  '개수':[10,20,30,40],
                  '당도':[30,50,70,90]}

dataFrame_Data = pd.DataFrame(dictionry_Data)
setIndexDataFrame = dataFrame_Data.set_index('이름') # 딕셔너리 내 '이름'를 인덱스로 지정
setIndexDataFrame += 10 # 모든 데이터에 10을 더하기
print(setIndexDataFrame)

Output
       가격  개수   당도
이름                
사과   1010  20   40
배    2010  30   60
딸기   3010  40   80
바나나  1510  50  100
```
- 데이터프레임(DataFrame) 객체와 데이터프레임(DataFrame) 객체 끼리 연산  

```python
import pandas as pd

dictionry_Data1 = {'이름':['사과','배','딸기','바나나'],
                  '가격':[1000,2000,3000,1500],
                  '개수':[10,20,30,40],
                  '당도':[30,50,70,90]}

dictionry_Data2 = {'이름':['사과','배','딸기','바나나'],
                  '가격':[100,200,300,150],
                  '개수':[1,2,3,4],
                  '당도':[3,5,7,9]}

dataFrame_Data1 = pd.DataFrame(dictionry_Data1)
dataFrame_Data2 = pd.DataFrame(dictionry_Data2)
setIndexDataFrame1 = dataFrame_Data1.set_index('이름') 
setIndexDataFrame2 = dataFrame_Data2.set_index('이름') 

#데이터 프레임끼리 같으면 바로 연산 가능
addDataFrame = setIndexDataFrame1 + setIndexDataFrame1 # +, -, *, / 다 가능
print(addDataFrame)

Output
       가격  개수   당도
이름                
사과   2000  20   60
배    4000  40  100
딸기   6000  60  140
바나나  3000  80  180
```
