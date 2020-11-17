# 문자열 함수

- 문자열은 큰따옴표(") 또는 작은 따옴표(')로 작성한다.  
- 문자열은 더하기(+)를 사용해서 문자열을 연결할 수 있다.  
- 문자열은 곱하기(*) 기호를 사용해서 반복으로 연결 할 수 있다.  
- len() 함수는 리스트나 문자열의 개수를 셀 때 사용한다.  

```Python  
testString1="큰 따옴표 " + "문자열 테스트"  
testString2='작은 따옴표 문자열 테스트,' * 2  

print(testString1)  
print(testString2)  
print(len(testString2))  

Output  
큰 따옴표 문자열 테스트  
작은 따옴표 문자열 테스트,작은 따옴표 문자열 테스트,  
30  
```  

## 함수와 메서드의 차이점  
- 함수는 단독으로 호출을 할 수 있다.  
- 메서드는 객체에 기능이 들어가 있어서 객체.메서드() 형식으로 사용된다.  

- 문자열 메서드 [대소문자 변환]  
| <center>메서드</center> | <center>설명</center>  
|:--------:|:--------:|      
|**<center>upper()</center>** |  <center>모든 문자열을 대문자로 변환한다.</center> |   
|**<center>lower()</center>** |  <center>모든 문자열을 소문자로 변환한다.</center> |   
|**<center>swapcase()</center>** |  <center>모든 문자열의 대문자는 소문자로, 소문자는 대문자로 변환한다.</center> |   
|**<center>title()</center>** |  <center>앞에 첫번째 문자만 대문자로 변환한다.</center> |   

```python  
testString = "Python 문자열 Test. 대소문자"  
print(testString.upper())  
print(testString.lower())  
print(testString.swapcase())  
print(testString.title())  

Output  
PYTHON 문자열 TEST. 대소문자  
python 문자열 test. 대소문자  
pYTHON 문자열 tEST. 대소문자  
Python 문자열 Test. 대소문자  
```  

- 문자열 메서드 [문자열 찾기]  
| <center>메서드</center> | <center>설명</center>  
|:--------:|:--------:|   
|**<center>count()</center>** |  <center>문자열 내 특정 문자열이 몇개 있는지 찾을 때</center> |   
|**<center>find()</center>** |  <center>문자열 내 특정 문자열의 첫번 째 위치를 찾을 때</center> |   
|**<center>rfind()</center>** |  <center>문자열 내 특정 문자열의 위치를 맨 오른쪽부터 찾을 때</center> |   
|**<center>index()</center>** |  <center>문자열 내 특정 문자열의 첫번 째 위치를 찾을 때</center> |   
|**<center>rindex()</center>** |  <center>문자열 내 특정 문자열의 위치를 맨 오른쪽부터 찾을 때</center> |   
|**<center>startswith()</center>** |  <center>문자열 내 시작 문자열이 특정 문자열과 일치하면 True, 아니면 False</center> |   
|**<center>endswith()</center>** |  <center>문자열 내 마지막 문자열이 특정 문자열과 일치하면 True, 아니면 False</center> |   

```python  
testString = "Python 문자열 Test. 문자열 찾기!!"  
print(testString.count("문자열"))  
print(testString.find("문자열"), testString.find("문자열", 12), testString.find("없는문자열"), end=",")  
print(testString.rfind("문자열"))  
print(testString.index("문자열"), testString.index("문자열", 12))  
print(testString.rindex("문자열"))  
print(testString.startswith("Python"), testString.startswith("Python", 12))  
print(testString.endswith("!!"))  

Output  
2  
7 17 -1  
17  
7 17  
17  
True False  
True  
```  

- 문자열 메서드 [공백 삭제,변경]  
| <center>메서드</center> | <center>설명</center>  
|:--------:|:--------:|      
|**<center>strip()</center>** |  <center>문자열 맨 앞과 뒤에 있는 공백 제거 또는 특정 문자를 삭제</center> |   
|**<center>rstrip()</center>** |  <center>문자열 맨 뒤에 있는 공백 제거 또는 특정 문자를 삭제</center> |   
|**<center>lstrip()</center>** |  <center>문자열 맨 앞에 있는 공백 제거 또는 특정 문자를 삭제</center> |   
|**<center>replace()</center>** |  <center>문자열 내 특정 문자열을 지정한 문자로 변경</center> |     

```python  
testString = "---Python 문자열 Test. 공백 삭제, 변경---"  
print(testString.strip('-'))  
print(testString.rstrip('-'))  
print(testString.lstrip('-'))  
print(testString.replace("Test", "테스트"))  

Output  
'Python 문자열 Test. 공백 삭제, 변경'  
'---Python 문자열 Test. 공백 삭제, 변경'  
'Python 문자열 Test. 공백 삭제, 변경---'  
'---Python 문자열 테스트. 공백 삭제, 변경---'  
```  

- 문자열 메서드 [분리, 결합, 대입]  
| <center>메서드</center> | <center>설명</center>  
|:--------:|:--------:|      
|**<center>split()</center>** |  <center>특정 문자 또는 공백을 기준으로 문자열을 잘라서 리스트에 저장</center> |   
|**<center>splitlines()</center>** |  <center>라인 단위로 문자열을 잘라서 리스트에 저장</center> |   
|**<center>join()</center>** |  <center>리스트를 특정 문자를 포함해 문자열로 변환</center> |    
|**<center>map()</center>** |  <center>문자열 리스트의 요소를 지정된 함수로 처리할 때</center> |    

```python  
testString = "Python 문자열 Test, 분리 결합 대입"  
print(testString.split())  
print(testString.split(','))  

testString = "Python \n문자열 \nTest \n분리 \n결합 \n대입"  
print(testString.splitlines())  

testString = '!'  
print(testString.join('Python'))  

# 문자로 저장된 숫자를 정수형으로 변환  
# map(함수,리스트)  
testString = ["2020", "11", "11"]  
print(list(map(int, testString)))  

Output  
['Python', '문자열', 'Test,', '분리', '결합', '대입']  
['Python 문자열 Test', ' 분리 결합 대입']  
['Python ', '문자열 ', 'Test ', '분리 ', '결합 ', '대입']  
P!y!t!h!o!n  
[2020, 11, 11]  
```  

- 문자열 메서드 [정렬, 채우기]  
| <center>메서드</center> | <center>설명</center>  
|:--------:|:--------:|      
|**<center>center()</center>** |  <center>문자열 가운데 정렬</center> |   
|**<center>ljust()</center>** |  <center>문자열 왼쪽 정렬</center> |   
|**<center>rjust()</center>** |  <center>문자열 오른쪽 정렬</center> |   
|**<center>zfill()</center>** |  <center>문자열 오른쪽 정렬, 나머지는 0으로 채움</center> |     

```python  
testString = "Python 문자열 Test. 정렬, 채우기"  
print(testString.center(30))  
print(testString.center(30, '-'))  
print(testString.ljust(30))  
print(testString.rjust(30))  
print(testString.zfill(30))  

Output  
'   Python 문자열 Test. 정렬, 채우기   '  
'---Python 문자열 Test. 정렬, 채우기---'  
'Python 문자열 Test. 정렬, 채우기      '  
'      Python 문자열 Test. 정렬, 채우기'  
'000000Python 문자열 Test. 정렬, 채우기'  
```  

- 문자열 메서드 [문자열 구성 파악]  
| <center>메서드</center> | <center>설명</center>  
|:--------:|:--------:|      
|**<center>isdigit()</center>** |  <center>해당 문자열이 전부 숫자로 되어 있으면 True, 아니면 False</center> |     
|**<center>isalpha()</center>** |  <center>해당 문자열이 전부 문자(한글,영어)로 되어 있으면 True, 아니면 False</center> |     
|**<center>isalnum()</center>** |  <center>해당 문자열이 전부 문자(한글,영어)와 숫자로 되어 있으면 True, 아니면 False</center> |     
|**<center>islower()</center>** |  <center>해당 문자열이 전부 소문자로 되어 있으면 True, 아니면 False</center> |     
|**<center>isupper()</center>** |  <center>해당 문자열이 전부 대문자로 되어 있으면 True, 아니면 False</center> |     
|**<center>isspace()</center>** |  <center>해당 문자열이 공백이나 개행, 탭이면 True, 아니면 False</center> |     

```python  
testString = "12345"  
print(testString.isdigit())  

testString = "PythonTest한글"  
print(testString.isalpha())  

testString = "12345PythonTest한글"  
print(testString.isalnum())  

testString = "python Test"  
print(testString.islower())  

testString = "PYTHON Test"  
print(testString.isupper())  

testString = "     "  
print(testString.isspace())  

Output  
True  
True  
True  
False  
False  
True  
```  
