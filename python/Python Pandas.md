# Python Pandas  
- python 대표 데이터 분석/처리 오픈소스 라이브러리로 필수적인 존재    
- 다양한 데이터에 대한 입출력, 변환, 선택, 결합, 클리닝, 그룹핑을 지원함    

## Pnadas의 주요 구성 요소  
- Pandas에서는 기본적으로 사용하는 객체는 DataFrame와 Series를 사용  
- 이 객체들은 빅 데이터 분석에 있어서 유용하게 사용할 수 있습니다.   

## Pandas 사용방법 : import pandas as pd    
- 기본적으로 pandas의 줄인 pd로 선언해서 사용함    

### Series : 벡터 데이터 객체  
- 리스트에 가까운 형식으로 1차원적으로 나열되어 있는 형태    
- 데이터 값(Value)과 인덱스(Index)가 함께 저장 됨    
- 키(Key)와 값(Value)이 "{Key:Value}" 형태의 쌍으로 이루어진 딕셔너리와 비슷한 형태  
- dtype은 각각의 컬럼에 대한 데이터 타입    
- 1개의 Column값으로만 구성된 1차원 데이터 셋  

#### Series 사용  
```python  
# dictionary -> series 변환  
import pandas as pd  
dic_Data = {'사과':1000, '배':2000, '바나나':3000}  
series_Data = pd.Series(dic_Data)  
print(type(series_Data))  
print(series_Data)    

Output  
<class 'pandas.core.series.Series'> # 타입은 Series  
사과   1000  
배      2000  
바나나 3000  
dtype: int64 # 데이터 타입  
```  

```python  
# list -> series 변환  
# list의 경우 키(Key)가 없기 때문에 인덱스(index)를 자동으로 0부터 시작해서 저장  
import pandas as pd  
list_Data = ['사과', 1000, '배', 2000, '바나나', 3000]  
series_Data = pd.Series(list_Data)  
print(type(series_Data))  
print(series_Data)  

Output  
<class 'pandas.core.series.Series'>  
0      사과  
1    1000  
2       배  
3    2000  
4     바나나  
5    3000  
dtype: object  
```  

### Index  
- 짝을 이루는 데이터 값의 순서와 주소를 저장  
- 인덱스 종류는 정수형 위치 인덱스, 인덱스 이름, 인덱스 라벨  
- Series 클래스의 index 속성을 이용하여 인덱스 배열을 따로 선택 가능 : Series객체.index  
- 데이터 값 배열만 따로 선택 : Series객체.value  

#### Index 사용  
```python  
# Series객체.index , Series객체.value 조회  
import pandas as pd  
dic_Data = {'사과':1000, '배':2000, '바나나':3000}  
series_Data = pd.Series(dic_Data)  
print(series_Data.index)  #Series객체.index   
print(series_Data.values) #Series객체.value  

Output  
Index(['사과', '배', '바나나'], dtype='object')  
[1000 2000 3000]  
```  

## 인덱싱(indexing)  
- 요소의 위치를 나타내는 인덱스를 이용하여 Series의 요소를 선택  
- 하나의 요소 선택, 여러 요소를 한꺼번에 선택  
- 파이썬의 리스트 슬라이싱 기법과 비슷하게 인덱스 범위를 지정하여 요소를 선택  
- 인덱스의 유형에 따라 사용법이 조금 다름  
- 인덱스 이름(라벨) : 대괄호 안에 이름과 함께 따옴표 입력, 쌍따옴표, 홀따옴표 모두 사용 가능  
 
#### Index 사용  
```python  
# tuple - > series로 변환 (인덱스 이름 지정)  
# series로 변환 후 인덱스로 조회  
import pandas as pd  
tuple_Data = ('사과', 1000, '2020-11-25')  
series_Data = pd.Series(tuple_Data, index=['이름', '가격', '생산일'])  
print(series_Data,"\n")  
print(series_Data[0], series_Data['이름'],"\n")  # 인덱스 명 또는 위치로 조회  
print(series_Data[[1,2]],"\n")  # 인덱스 위치를 리스트 형태로 지정 후 조회   
print(series_Data[['가격','생산일']],"\n") # 인덱스 명을 리스트 형태로 지정 후 조회  
print(series_Data[1:2],"\n")  # 인덱스 위치를 범위 형태로 지정 후 조회   
print(series_Data['가격':'생산일']) # 인덱스 명으로 범위 조회 시 지정한 인덱스 명까지 조회  

Output  
이름             사과  
가격           1000  
생산일    2020-11-25  
dtype: object   

사과 사과   

가격           1000  
생산일    2020-11-25  
dtype: object   

가격           1000  
생산일    2020-11-25  
dtype: object   

가격    1000  
dtype: object   

가격           1000  
생산일    2020-11-25  
dtype: object  
​```  

### DataFrame : 테이블 데이터 객체  
- 테이블 형식으로 되어 있는 데이터를 DataFrame 라고 지칭함    
- 데이터 프레임의 열은 각각 Series 객체  
- Column X Row 2차원 데이터 셋  
- Column값과 Row 값 그리고 Index가 존재함   

#### DataFrame 사용  
```python  
# dictionary -> DataFrame 변환 (list, tuple도 가능)  
# Index의 경우는 지정하지 않았기에 0부터 시작해서 저장  
import pandas as pd  
dic_Data = {'사과':[1000,'2020-11-25'], '배':[2000,'2020-11-24'], '바나나':[3000,'2020-11-20']}  
dataFrame_Data = pd.DataFrame(dic_Data)  
print(type(dataFrame_Data))  
print(dataFrame_Data)  

Output  
<class 'pandas.core.frame.DataFrame'> # 타입은 DataFrame  
           사과           배         바나나  
0        1000        2000        3000  
1  2020-11-25  2020-11-24  2020-11-20  
```

#### 행 인덱스/열 이름 설정  
- index, columns 지정 : pd.DataFrame(데이터, index=[], columns[])  

```python  
# 행 인덱스/열 이름 설정  
import pandas as pd  
dataFrame_Data = pd.DataFrame([[1000,'2020-11-25', 5],   
                               [2000,'2020-11-24', 3],   
                               [3000,'2020-11-20', 7]],  
                              index=['사과', '배', '바나나'],  
                              columns=['가격', '생산일', '남은 개수'])  

print(type(dataFrame_Data))  
print(dataFrame_Data)  
print(dataFrame_Data.index)  
print(dataFrame_Data.columns)  

Output  
<class 'pandas.core.frame.DataFrame'>  
       가격         생산일  남은 개수  
사과   1000  2020-11-25      5  
배    2000  2020-11-24      3  
바나나  3000  2020-11-20      7  
Index(['사과', '배', '바나나'], dtype='object') # index  
Index(['가격', '생산일', '남은 개수'], dtype='object') # columns  
```  

#### 행 인덱스/열 이름 통채로 변경  
- index 변경 : DataFrame객체.index=새로운 행 인덱스 배열  
- column 변경 : DataFrame객체.columns=새로운 열 이름 배열  
 
```python  
# 행 인덱스/열 이름 설정  
import pandas as pd  
dataFrame_Data = pd.DataFrame([[1000,'2020-11-25', 5],   
                               [2000,'2020-11-24', 3],   
                               [3000,'2020-11-20', 7]],  
                              index=['사과', '배', '바나나'],  
                              columns=['가격', '생산일', '남은 개수'])  

print(dataFrame_Data.index)  
print(dataFrame_Data.columns)  
dataFrame_Data.index=['딸기', '귤', '오렌지']  
dataFrame_Data.columns=['금액', '유통기한', '판매 개수']  
print(dataFrame_Data.index)  
print(dataFrame_Data.columns)  

Output  
Index(['사과', '배', '바나나'], dtype='object')  
Index(['가격', '생산일', '남은 개수'], dtype='object')  
Index(['딸기', '귤', '오렌지'], dtype='object')  
Index(['금액', '유통기한', '판매 개수'], dtype='object')  
```  

#### 행 인덱스/열 이름 부분 변경  
- inplace : 해당 DataFrame객체내 있는 index 또는 cloumns를 변경하려면 TRUE, 그렇지 않으면 FALSE, 기본은 FALSE  
- index 변경 : DataFrame객체.rename(index = {기존 인덱스:새 인덱스}, inplace=True)  
- column 변경 : DataFrame객체.rename(columns={기존 이름:새 이름}, inplace=True)  

```python  
# 행 인덱스/열 이름 변경  
import pandas as pd  
dataFrame_Data = pd.DataFrame([[1000,'2020-11-25', 5],   
                               [2000,'2020-11-24', 3],   
                               [3000,'2020-11-20', 7]],  
                              index=['사과', '배', '바나나'],  
                              columns=['가격', '생산일', '남은 개수'])  

print(dataFrame_Data.index)  
print(dataFrame_Data.columns)  
dataFrame_Data.rename(index={'사과':'딸기'}, columns={'남은 개수':'판매 개수'} , inplace=True)  
print(dataFrame_Data.index)  
print(dataFrame_Data.columns)  

Output  
Index(['사과', '배', '바나나'], dtype='object')  
Index(['가격', '생산일', '남은 개수'], dtype='object')  
Index(['딸기', '배', '바나나'], dtype='object')  
Index(['가격', '생산일', '판매 개수'], dtype='object')  
```  

#### 행 /열 삭제  
- 행 삭제 : DataFrame객체.drop(행 인덱스 또는 배열, axis=0)  
- 열 삭제 : DataFrame객체.drop(열 이름 또는 배열, axis=1)  
- 행 다중 삭제 : DataFrame객체.drop([행,행,..], axis=0)  
- 열 다중 삭제  : DataFrame객체.drop([열,열,..], axis=1)  

```python  
# 행 인덱스/열 이름 삭제  
import pandas as pd  
dataFrame_Data = pd.DataFrame([[1000,'2020-11-25', 5],   
                               [2000,'2020-11-24', 3],   
                               [3000,'2020-11-20', 7]],  
                              index=['사과', '배', '바나나'],  
                              columns=['가격', '생산일', '남은 개수'])  

print(dataFrame_Data.index)  
print(dataFrame_Data.columns)  
dataFrame_Data.drop('사과', axis=0, inplace=True)  
dataFrame_Data.drop('가격', axis=1, inplace=True)  
print(dataFrame_Data.index)  
print(dataFrame_Data.columns)  
print(dataFrame_Data)  

Output  
Index(['사과', '배', '바나나'], dtype='object')  
Index(['가격', '생산일', '남은 개수'], dtype='object')  
Index(['배', '바나나'], dtype='object')  
Index(['생산일', '남은 개수'], dtype='object')  
            생산일  남은 개수  
배    2020-11-24      3  
바나나  2020-11-20      7  
```    

```python  
# 행 인덱스/열 이름 다중  
import pandas as pd  
dataFrame_Data = pd.DataFrame([[1000,'2020-11-25', 5],   
                               [2000,'2020-11-24', 3],   
                               [3000,'2020-11-20', 7]],  
                              index=['사과', '배', '바나나'],  
                              columns=['가격', '생산일', '남은 개수'])  

print(dataFrame_Data.index)  
print(dataFrame_Data.columns)  
dataFrame_Data.drop(['사과','바나나'], axis=0, inplace=True)  
dataFrame_Data.drop(['가격','생산일'], axis=1, inplace=True)  
print(dataFrame_Data.index)  
print(dataFrame_Data.columns)  
print(dataFrame_Data)  

Output  
Index(['사과', '배', '바나나'], dtype='object')  
Index(['가격', '생산일', '남은 개수'], dtype='object')  
Index(['배'], dtype='object')  
Index(['남은 개수'], dtype='object')  
   남은 개수  
배      3  
```  

### 행 선택  
- DataFrame의 행 데이터를 선택 시 loc와 iloc 사용  
- 인덱스 이름(index label)을 기준으로 행을 선택할 때 loc 사용  
- 정수형 위치 인덱스(interger position)를 기준으로 행을 선택할 때 iloc 사용  
- loc의 범위 지정 시 범위의 끝을 포함하여 선택 : DataFrame객체.loc['a':'c'] -> 'a','b','c'  
- iloc의 범위 지정 시 범위의 끝은 제외하고 선택 : DataFrame객체.iloc[1:3] -> 1,2  

```python  
# 인덱스 이름(index label), 정수형 위치 인덱스(interger position)으로 행 단일 선택  
import pandas as pd  
dataFrame_Data = pd.DataFrame([[1000,'2020-11-25', 5],   
                               [2000,'2020-11-24', 3],   
                               [3000,'2020-11-20', 7]],  
                              index=['사과', '배', '바나나'],  
                              columns=['가격', '생산일', '남은 개수'])  

label_Data = dataFrame_Data.loc['사과']  
print(label_Data)  
print(type(label_Data), "\n")  
pos_Data = dataFrame_Data.iloc[0]  
print(pos_Data)  
print(type(pos_Data))  

Output  
가격             1000  
생산일      2020-11-25  
남은 개수             5  
Name: 사과, dtype: object  
<class 'pandas.core.series.Series'>  # 단일은 Series로 받는다.  

가격             1000  
생산일      2020-11-25  
남은 개수             5  
Name: 사과, dtype: object   
<class 'pandas.core.series.Series'> # 단일은 Series로 받는다.  
```  

```python  
# 인덱스 이름(index label), 정수형 위치 인덱스(interger position)으로 행 멀티 선택  
import pandas as pd  
dataFrame_Data = pd.DataFrame([[1000,'2020-11-25', 5],   
                               [2000,'2020-11-24', 3],   
                               [3000,'2020-11-20', 7]],  
                              index=['사과', '배', '바나나'],  
                              columns=['가격', '생산일', '남은 개수'])  

label_Data = dataFrame_Data.loc[['사과','바나나']]  
print(label_Data)  
print(type(label_Data), "\n")  
pos_Data = dataFrame_Data.iloc[[0,2]]  
print(pos_Data)  
print(type(pos_Data))  

Output  
       가격         생산일  남은 개수  
사과   1000  2020-11-25      5  
바나나  3000  2020-11-20      7  
<class 'pandas.core.frame.DataFrame'> # 멀티는 DataFrame로 받는다.  

       가격         생산일  남은 개수  
사과   1000  2020-11-25      5  
바나나  3000  2020-11-20      7  
<class 'pandas.core.frame.DataFrame'>  # 멀티는 DataFrame로 받는다.  
```  

```python  
# 인덱스 이름(index label), 정수형 위치 인덱스(interger position)으로 행 범위 선택  
import pandas as pd  
dataFrame_Data = pd.DataFrame([[1000,'2020-11-25', 5],   
                               [2000,'2020-11-24', 3],   
                               [3000,'2020-11-20', 7]],  
                              index=['사과', '배', '바나나'],  
                              columns=['가격', '생산일', '남은 개수'])  

label_Data = dataFrame_Data.loc['사과':'바나나']  
print(label_Data)  
print(type(label_Data), "\n")  
pos_Data = dataFrame_Data.iloc[0:2]  
print(pos_Data)  
print(type(pos_Data))  

Output  
       가격         생산일  남은 개수  
사과   1000  2020-11-25      5  
배    2000  2020-11-24      3  
바나나  3000  2020-11-20      7  
<class 'pandas.core.frame.DataFrame'> # 멀티는 DataFrame로 받는다.  

      가격         생산일  남은 개수  
사과  1000  2020-11-25      5  
배   2000  2020-11-24      3  
<class 'pandas.core.frame.DataFrame'> # 멀티는 DataFrame로 받는다.  
```  

### 열 선택  
- 열 1개를 선택 시 DataFrame객체['열 이름'], 또는 DataFrame객체.열 이름  
- 여러개의 열 선택 시 DataFrame객체[['열 이름','열 이름',...]]  

```python  
# 열 선택  
import pandas as pd  
dataFrame_Data = pd.DataFrame([[1000,'2020-11-25', 5],   
                               [2000,'2020-11-24', 3],   
                               [3000,'2020-11-20', 7]],  
                              index=['사과', '배', '바나나'],  
                              columns=['가격', '생산일', '남은 개수'])  

single_colmn_Data = dataFrame_Data['가격']  
print(single_colmn_Data)  
print(type(single_colmn_Data), "\n")  
multi_colmn_Data = dataFrame_Data[['가격','남은 개수']]  
print(multi_colmn_Data)  
print(type(multi_colmn_Data))  

Output  
사과     1000  
배      2000  
바나나    3000  
Name: 가격, dtype: int64  
<class 'pandas.core.series.Series'> # 단일은 Series  

       가격  남은 개수  
사과   1000      5  
배    2000      3  
바나나  3000      7  
<class 'pandas.core.frame.DataFrame'> # 멀티는 DataFrame  
```  

### 요소 선택  
- DataFrame의 행 인덱스와 열 이름을 [행,열] 형식의 2차원 좌표로 입력하여 요소 위치를 지정  
- 요소가 위치하는 행과 열의 좌표를 입력하면 해당 위치의 원소가 반환  
- 1개의 행과 2개 이상의 열을 선택하거나 2개 이상의 행과 1개의 열을 선택하면 Series 객체가 반환  
- 2개 이상의 행과 열을 선택하면 DataFrame 객체를 반환  
- 인덱스 이름을 사용하여 요소 선택 : DataFrame객체.loc[행 인덱스, 열 이름]  
- 정수 위치 인덱스를 사용하여 요소 선택 : DataFrame객체.iloc[행 번호, 열 번호]  

```python  
import pandas as pd  
dataFrame_Data = pd.DataFrame([[1000,'2020-11-25', 5],   
                               [2000,'2020-11-24', 3],   
                               [3000,'2020-11-20', 7]],  
                              index=['사과', '배', '바나나'],  
                              columns=['가격', '생산일', '남은 개수'])  

# 인덱스 이름을 사용하여 요소 선택  
name_Data1 = dataFrame_Data.loc['사과','가격']  
print(name_Data1)  
print(type(name_Data1), "\n")  

# 정수 위치 인덱스를 사용하여 요소 선택  
name_Data2 = dataFrame_Data.iloc[0,1]  
print(name_Data2)  
print(type(name_Data2), "\n")  

# 인덱스 이름을 사용하여 특정 원소 행/열 2개 이상 선택  
name_Data3 = dataFrame_Data.loc[['사과','배'],['가격','남은 개수']]  
print(name_Data3)  
print(type(name_Data3), "\n")  

# 정수 위치 인덱스를 사용하여 특정 원소 2개 이상 선택  
name_Data4 = dataFrame_Data.iloc[0,[0,2]]  
print(name_Data4)  
print(type(name_Data4), "\n")  

Output  
1000  
<class 'numpy.int64'>   

1000  
<class 'numpy.int64'>   

      가격  남은 개수  
사과  1000      5  
배   2000      3  
<class 'pandas.core.frame.DataFrame'>   

가격       1000  
남은 개수       5  
Name: 사과, dtype: object  
<class 'pandas.core.series.Series'>   
```  

### 열 추가  
- DataFrame객체['추가하려는 열 이름'] = 데이터 값 or 배열  

```python  
import pandas as pd  
dataFrame_Data = pd.DataFrame([[1000,'2020-11-25', 5],   
                               [2000,'2020-11-24', 3],   
                               [3000,'2020-11-20', 7]],  
                              index=['사과', '배', '바나나'],  
                              columns=['가격', '생산일', '남은 개수'])  

dataFrame_Data['판매 개수'] = 5  
print(dataFrame_Data)  

Output  
  	가격        생산일	 남은 개수  판매 개수  
사과	1000  2020-11-25	           5           5  
배	2000  2020-11-24	           3           5  
바나나	3000  2020-11-20	           7           5  
```  

### 행 추가  
- DataFrame객체.loc['추가하려는 행 이름'] = 데이터 값 or 배열  

```python  
import pandas as pd  
dataFrame_Data = pd.DataFrame([[1000,'2020-11-25', 5],   
                               [2000,'2020-11-24', 3],   
                               [3000,'2020-11-20', 7]],  
                              index=['사과', '배', '바나나'],  
                              columns=['가격', '생산일', '남은 개수'])  

dataFrame_Data.loc['오렌지']=[1500, '2020-11-17', 6]  
print(dataFrame_Data)  

Output  
          가격         생산일  남은 개수  
사과    1000  2020-11-25            5  
배       2000  2020-11-24            3  
바나나  3000  2020-11-20            7  
오렌지  1500  2020-11-17            6  
```  

### 요소 값 변경  
- DataFrame객체의 일부분 또는 원소를 선택 = 데이터 값  

```python  
import pandas as pd  
dataFrame_Data = pd.DataFrame([[1000,'2020-11-25', 5],   
                               [2000,'2020-11-24', 3],   
                               [3000,'2020-11-20', 7]],  
                              index=['사과', '배', '바나나'],  
                              columns=['가격', '생산일', '남은 개수'])  

dataFrame_Data.loc['사과','가격'] = 5000 # 1000 -> 5000 변경  
dataFrame_Data.iloc[1,0] = 8000 # 2000 -> 8000 변경  
# dataFrame_Data.loc['사과',['가격','남은 개수']] = 1000, 8 # 가격=1000, 남은 개수=8  
# dataFrame_Data.loc['사과',['가격','남은 개수']] = 500 # 가격=500, 남은 개수=500  
# dataFrame_Data.iloc[1,[1,2]] = '2020-11-16', 13 # 생산일='2020-11-16', 남은 개수=13  
print(dataFrame_Data)  

Output  
          가격         생산일  남은 개수  
사과    5000  2020-11-25            5  
배       8000  2020-11-24            3  
바나나  3000  2020-11-20            7  
```  

### 행/열 위치 바꾸기  
- 선형 대수의 전치행렬과 비슷한 개념  
- DataFrame객체.transpose()  
- DataFrame객체.T  

```python  
import pandas as pd  
dataFrame_Data = pd.DataFrame([[1000,'2020-11-25', 5],   
                               [2000,'2020-11-24', 3],   
                               [3000,'2020-11-20', 7]],  
                              index=['사과', '배', '바나나'],  
                              columns=['가격', '생산일', '남은 개수'])  

dataFrame_Data = dataFrame_Data.transpose()  
# dataFrame_Data = dataFrame_Data.T  
print(dataFrame_Data)  

Output  
               사과           배         바나나  
가격           1000        2000        3000  
생산일    2020-11-25  2020-11-24  2020-11-20  
남은 개수           5           3           7  
```  