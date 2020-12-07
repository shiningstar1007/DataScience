# Python Pandas-파일읽기  
- CSV, Excel, JSON, HTML 같은 여러 형태의 파일을 읽어서 데이터프레임으로 변환 할 수 있음  

## CSV 파일 (Comma-Separated Values)  
- 데이터 값을 쉼표(,)로 구분하고 있음  
- 쉼표(,)로 열을 구분하고 줄바꿈으로 행을 구분함  
- 쉼표(,) 대신 탭(\t)이나 공백(' ')으로 텍스트를 구분할수도 있음  
- 이럴땐 구분자(sep 또는 delimiter) 옵션을 알맞게 입력해야 함  

### CSV 파일 읽기 함수  
- read_csv() 함수를 사용하여 CSV 파일을 읽을 수 있음  

#### read_csv() 함수 옵션  
- path : 파일의 전체 경로, URL  
- names : 열 이름으로 사용할 문자열의 리스트  
- header : 열 이름으로 사용될 행의 번호(default : 0), header가 없고 첫 행부터 데이터가 있는 경우에는 None으로 지정 가능   
- index_col : 행 인덱스로 사용될 열의 번호 또는 열 이름  
- sep(또는 delimiter) : 텍스트 데이터를 필드별로 구분하는 문자  
- skiprows : 처음 몇 줄을 skip할 것인지 설정, skip하려는 행의 번호를 담은 리스트로 설정 가능  
- skip_footer : 마지막 몇줄을 skip할 것인지 설정  
- parse_dates : 날짜 텍스트를 datetime64로 변환할 것인지 설정 (default : false)  
- encoding : 텍스트 인코딩 지정 ('utf-8', 'ANSI', ...)  

```csv
# csv_sample.csv
과일이름,과일가격,판매개수,남은개수
배,100,14,7
사과,200,15,8
딸기,300,16,9
```

```python
import pandas as pd

csvName="csv_sample.csv"

dataFrame_data = pd.read_csv(csvName)

print(dataFrame_data)
print(type(dataFrame_data))

Output
  과일이름  과일가격  판매개수  남은개수
0    배   100    14     7
1   사과   200    15     8
2   딸기   300    16     9
<class 'pandas.core.frame.DataFrame'>

# pd.read_csv(csvName, index_col="과일이름")
dataFrame_data = pd.read_csv(csvName, index_col="과일이름")

print(dataFrame_data)

Output
      과일가격  판매개수  남은개수
과일이름                  
배      100    14     7
사과     200    15     8
딸기     300    16     9
```

## JSON 파일  
- JSON 파일의 확장자는 .json  
- JSON은 데이터 공유를 목적으로 개발된 특수한 파일 형식  
- JSON은 key:value 구조를 가지고 있으며, 구조가 중첩되는 방식에 따라 옵션을 다르게 적용함  

### JSON 파일 읽기 함수  
- read_json() 함수를 사용하여 JSON 파일을 읽을 수 있음  

```json
{
    "req": {
      "instance": "Test_Python",
      "name": "Python",
      "user": "user1"
    },
    "param": {
      "instance": "check",
      "name": "compare",
      "user": "permission"
    },
    "res": {
    "instance": "True",
    "name": "True",
    "user": "false"
    }
}
```

```python
import pandas as pd

jsonName='json_sample.json'

dataFrame_data = pd.read_json(jsonName)

print(dataFrame_data)
print(type(dataFrame_data))

Output
                  req       param    res
instance  Test_Python       check   True
name           Python     compare   True
user            user1  permission  false
<class 'pandas.core.frame.DataFrame'>
```

## Excel 파일  
- 흔히 많이 사용하는 MS Excel 파일로 저장되어 있음  
- 테이블 구조 형태로 저장되어 있기에 DataFrame 과 유사함  

### Excel 파일 읽기 함수  
- read_excel() 함수를 사용하여 Excel 파일을 읽을 수 있음  

#### Excel 읽기 시도 시 에러 발생  
- Missing optional dependency 'xlrd'. Install xlrd >= 1.0.0 for Excel support Use pip or conda to install xlrd.   

#### 해결 방법  
- pip install xlrd   

```python
import pandas as pd

excelName='excel_sample.xlsx'

dataFrame_data = pd.read_excel(excelName)

print(dataFrame_data)
print(type(dataFrame_data))

Output
   수출국가 수출품목  2013  2014  2015  2016  2017  2018  2019  2020
0   남한   합계  1065  1292  1526  1765  1922  2195  2461  3407
1  NaN  반도체   529   663   765   881  1022  1122  1264  1864
2  NaN   철강   484   573   696   803   813   903   953  1195
3  NaN  식음료    52    56    65    81    87   170   239   337
4  NaN   원유     -     -     -     -     -     -     5    11
5   북한   합계   244   263   347   321   331   353   448   432
6  NaN   철강   156   150   242   233   238   242   325   335
7  NaN  식음료    88   113   105    88    93   111   123    97
8  NaN   원유     -     -     -     -     -     -     -     -
<class 'pandas.core.frame.DataFrame'>
```
