# Python Pandas - Index 활용

## 특정 열을 행 인덱스로 설정
- 데이터프레임 객체.set_index(['열이름']또는 '열이름)

```python
# set_index를 사용하여 특정 열(column)을 데이터프레임의 행 Index로 설정
import pandas as pd
dataFrame_Data = pd.DataFrame({'과일' : ['사과', '배', '바나나'],
                               '가격' : [1000, 2000, 3000],
                               '판매개수' : [10, 20, 15],
                               '남은개수' : [100, 150, 70]})

print(dataFrame_Data, "\n")
priceIndex = dataFrame_Data.set_index(['가격'])
print(priceIndex)

Output
    과일    가격  판매개수  남은개수
0   사과  1000    10   100
1    배  2000    20   150
2  바나나  3000    15    70 

       과일  판매개수  남은개수
가격                   
1000   사과    10   100
2000    배    20   150
3000  바나나    15    70
```

## 행 인덱스 재배열
- 새로운 배열로 행 인덱스를 재지정 : DataFrame객체.reindex(새로운 인덱스 배열)
- 기존 데이터 프레임에 존재하지 않는 행 인덱스가 새로 추가되는 경우 그 행의 데이터 값은 NaN(Not a Number)값이 입력

### NaN[Not a Number (Missing value)] : 결측값  
- "어떤 값이 존재하지 않을 때" 를 지칭  
|  <center>타입</center> |  <center>설명</center> |   
|:--------:|:--------:|  
|**<center>isnull()</center>** | <center>NaN이 있는지 여부(True/False)</center> |  
|**<center>fillna()</center>** | <center>NaN이 있는 행/열 대치</center> |  
|**<center>dropna()</center>** | <center>NaN이 있는 행/열 삭제</center> |  

```python
# reindex를 사용하여 데이터프레임의 행 Index를 재 설정
import pandas as pd
dictionry_Data = {'col0':[1,2,3], 'col1':[4,5,6], 'col2':[7,8,9], 'col3':[10,11,12]}
dataFrame_Data = pd.DataFrame(dictionry_Data, index=['row0', 'row1', 'row2'])

print(dataFrame_Data, "\n")
new_Index = dataFrame_Data.reindex(['row0','row1','row2','row3','row4'])
print(new_Index, "\n")

# reindex를 사용하여 발생한 NaN값을 다른 값으로 지정 
# fill_value 옵션을 사용하여 설정 가능 : fill_value=값
new_Index = dataFrame_Data.reindex(['row0','row1','row2','row3','row4'], fill_value=0)
print(new_Index)

Output
      col0  col1  col2  col3
row0     1     4     7    10
row1     2     5     8    11
row2     3     6     9    12 

      col0  col1  col2  col3
row0   1.0   4.0   7.0  10.0
row1   2.0   5.0   8.0  11.0
row2   3.0   6.0   9.0  12.0
row3   NaN   NaN   NaN   NaN
row4   NaN   NaN   NaN   NaN

      col0  col1  col2  col3
row0     1     4     7    10
row1     2     5     8    11
row2     3     6     9    12
row3     0     0     0     0
row4     0     0     0     0
```

## 행 인덱스 초기화
- 정수형 위치 인덱스로 초기화 : DataFrame객체.reset_index()

```python
# reset_index를 사용하여 행 인덱스를 정수형으로 초기화
import pandas as pd
dictionry_Data = {'col0':[1,2,3], 'col1':[4,5,6], 'col2':[7,8,9], 'col3':[10,11,12]}
dataFrame_Data = pd.DataFrame(dictionry_Data, index=['row0', 'row1', 'row2'])

print(dataFrame_Data, "\n")
integer_Index = dataFrame_Data.reset_index()
print(integer_Index)

Output
      col0  col1  col2  col3
row0     1     4     7    10
row1     2     5     8    11
row2     3     6     9    12 

  index  col0  col1  col2  col3
0  row0     1     4     7    10
1  row1     2     5     8    11
2  row2     3     6     9    12
```

## 행 인덱스를 기준으로 데이터프레임 정렬
- 행 인덱스 기준 정렬 : DataFrame객체.sort_index()
- ascending 옵션 : 오름차순(True) 또는 내림차순(False)설정

```python
# sort_index를 사용하여 행 인덱스를 정렬
import pandas as pd
dictionry_Data = {'col0':[1,2,3], 'col1':[4,5,6], 'col2':[7,8,9], 'col3':[10,11,12]}
dataFrame_Data = pd.DataFrame(dictionry_Data, index=['row0', 'row1', 'row2'])

ascending_Data = dataFrame_Data.sort_index(ascending=True)
descending_Data = dataFrame_Data.sort_index(ascending=False)
print(ascending_Data, "\n")
print(descending_Data)

Output
      col0  col1  col2  col3
row0     1     4     7    10
row1     2     5     8    11
row2     3     6     9    12 

      col0  col1  col2  col3
row2     3     6     9    12
row1     2     5     8    11
row0     1     4     7    10
```

## 특정 열의 데이터 값을 기준으로 데이터프레임 정렬
- 열 기준 정렬 : DataFrame객체.sort_values()

```python
# sort_values를 사용하여 특정 열의 데이터 값을 기준으로 정렬
# sort_value(by=None,         # 정렬할 기준 열(Columns))
#            axis=0,               # 0 or 'index', columns
#            ascending=True,   #True:오름차순, False:내림차순
#            inplace=False,      #DataFrame 자체를 정렬해서 저장
#            kind='quicksort',   # 정렬 알고리즘
#            na_position='last') #결측값 위치, {'first', 'last'}
import pandas as pd
dictionry_Data = {'col0':[1,2,3], 'col1':[6,5,4], 'col2':[7,8,9], 'col3':[10,11,12]}
dataFrame_Data = pd.DataFrame(dictionry_Data, index=['row0', 'row1', 'row2'])

columnSort_Data = dataFrame_Data.sort_values(by='col1')
print(columnSort_Data)

Output
      col0  col1  col2  col3
row0     1     6     7    10
row1     2     5     8    11
row2     3     4     9    12 

      col0  col1  col2  col3
row2     3     4     9    12
row1     2     5     8    11
row0     1     6     7    10
```
