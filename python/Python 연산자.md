# 연산자

## 산술 연산자  
| <center>연산자</center> | <center>사용 방법</center> | <center>설명</center>  
|:--------:|:--------:|:--------:|      
|**<center> + </center>** |  <center>2+3</center> |  <center>정수 2와 3을 더하기</center> |  
|**<center> - </center>** | <center>2-1</center> | <center>2에서 1을 빼기</center> |  
|**<center> * </center>** | <center>2*3</center> | <center>2와 3을 곱하기</center> |  
|**<center> ** </center>** |  <center>2**3</center> | <center>2의 3제곱</center> |  
|**<center> / </center>** | <center>2/1</center> |  <center>2를 1로 나누기</center> |  
|**<center> // </center>** |  <center>2//1</center> |  <center>2를 1로 나눈 몫</center> |  
|**<center> % </center>** | <center>2%1</center> |  <center>2를 1로 나눈 후 나머지 값</center> |  

## 대입 연산자   
- C/C++ 등의 언어에 있는 증가 연산자(++)나 감소 연산자(--)가 파이썬에서는 없다.   

| <center>연산자</center> | <center>사용 방법</center> | <center>설명</center>  
|:--------:|:--------:|:--------:|      
|**<center>=</center>** | <center>value = 3</center> | <center> value에 정수 3을 대입</center> |  
|**<center>+=</center>** |  <center>value += 3</center> |  <center>value와 정수 3을 더한 후 value에 대입</center> |  
|**<center>-=</center>** | <center>value -= 3</center> | <center>value에서 정수 3을 뺀 후 value에 대입</center> |  
|**<center>*=</center>** | <center>value *= 3</center> | <center>value와 정수 3을 곱한 후 value에 대입</center> |  
|**<center>**=</center>** |  <center>value **= 3</center> | <center>value의 3제곱을 구한 후 value에 대입</center> |  
|**<center>/= </center>** | <center>value /= 3</center> |  <center>value를 정수 3으로 나눈 후 value에 대입</center> |  
|**<center>//=</center>** |  <center>value //= 3</center> |  <center>value를 정수 3으로 나눈 몫을 value에 대입</center> |  
|**<center>%=</center>** | <center>value %= 3</center> |  <center>value를 정수 3으로 나눈 후 나머지 값을 value에 대입</center> |  

## 관계 연산자 
- 어떤 값이 크거나 작거나 같은지 비교하여 참(True),거짓(False)으로 표현  
- 조건문(if) 또는 반복문(while) 같이 참,거짓을 필요로 할 때 사용  

| <center>연산자</center> | <center>사용 방법</center> | <center>설명</center>  
|:--------:|:--------:|:--------:|      
|**<center> ==</center>** | <center>value == 3</center> | <center>value와 3이 같으면 참, 아니면 거짓</center> |   
|**<center> != </center>** | <center>value != 3</center> | <center>value와 3이 다르면 참, 아니면 거짓</center> |   
|**<center> >= </center>** | <center>value >= 3</center> | <center>value가 3보다 크거나 같으면 참, 아니면 거짓</center> |   
|**<center> <= </center>** | <center>value <= 3</center> | <center>value가 3보다 작거나 같으면 참, 아니면 거짓</center> |   
|**<center> > </center>** | <center>value > 3</center> | <center>value가 3보다 크면 참, 아니면 거짓</center> |   
|**<center> < </center>** | <center>value < 3</center> | <center>value가 3보다 작으면 참, 아니면 거짓</center> |   

## 논리 연산자 
| <center>연산자</center> | <center>사용 방법</center> | <center>설명</center>  
|:--------:|:--------:|:--------:|      
|**<center> and </center>** | <center>(value1 == 3) and (value2 == 1)</center> | <center>조건 2개가 모두 참이면 참, 아니면 거짓</center> |  
|**<center> or </center>** | <center>(value1 == 3) or (value2 == 1)</center> | <center>조건 2개 중 하나만 참이면 참</center> |  
|**<center> not </center>** | <center>not(value1 == 3)</center> | <center>해당 조건이 참이면 거짓, 거짓이면 참</center> | 

## 문자열을 숫자로 변경 하는 방법  
int() : 문자열을 정수로 변환  
float() : 문자열을 실수로 변환  

```Python  
Input  
intString1 = "10"  
floatString1 = "10.23"  
print(int(intString1) + 1, float(floatString1) + 1)  

OutPut  
11 11.23  
```  

## 숫자를 문자열로 변경 하는 방법  
str(): 숫자를 문자열로 변환  

```Python  
Input  
intValue1 = 10  
floatValue1 = 10.23  
str(intValue1), str(floatValue1)  

OutPut  
('10', '10.23')  
```  

여기서 print() 함수를 사용 하지 않은 이유는 출력 메시지에 ''가 없어서 문자열인지 구분 할 수 없어서 사용하지 않음  
