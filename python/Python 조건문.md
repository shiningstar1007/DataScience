# 조건문
- 파이썬은 들여쓰기가 매우 중요하다.  

## if ~ else 문  
- if ~else 문 작성 시 다음에 실행할 문장은 if문 다음 줄에서 들여쓰기를 해서 작성해야 한다.  
- 들여쓰기를 작성 안하면 조건문에 대한 실행문이 실행되지 않는다.  
- 실행문이 2개 이상일 때는 들여쓰기를 맞춰서 작성하면 된다.  
- 작성 방법은 if ~ elif ~else 작성 후 조건식을 작성하고 마지막에 : 을 작성해야 한다.  

```Python  
if : 해당 조건문이 참이면  
elif : 위 조건문이 거짓이고 해당 조건문이 참이면  
else : 위 조건문이 거짓이면  
```

### if 문 실행에 대한 실행문 2개 (X)  
```Python  
value = 30  
if value < 20 :  
    print("value는 20보다 작다.")   
print("해당 조건은 참")  

Output  
해당 조건은 참  
```  

### if ~ else 실행에 대한 실행문 1개 (O)  
```Python  
value = 10  
if value < 20 :  
    print("value는 20보다 작다.") # 참  
else :  
    print("value는 20보다 크다.") # 거짓  

Output  
value는 20보다 작다.  
```  

### 조건문 실행에 대한 실행문 2개  
```Python  
value = 10  
if value < 20 :  
    print("value는 20보다 작다.")  
    print("해당 조건은 참")  
else :  
    print("value는 20보다 크다.")  
    printf("해당 조건은 거짓")  

Output  
value는 20보다 작다.  
해당 조건은 참  
```  

### 삼항 연산자를 사용한 if ~ else 문  
- value 가 80보다 크거나 같으면 '통과', 아니면 '탈락'을 stringRes에 대입  
```Python  
value = 90  
stringRes = '통과' if value >= 80 else '탈락'  
```  

### in, not in을 활용한 if 문  
- 특정한 문자열 내 찾고자 하는 문자열이 있는지 검색 할 때 사용   
- in 은 찾고자 하는 문자열이 있으면 True를 리턴한다.  
- not in 은 찾고자 하는 문자열이 있으면 False를 리턴한다.  
```Python  
money = ['5만원', '1만원' , '5천원', '1천원']  

if '5만원' in money :  
    print("5만원을 가지고 있다.")  

Output  
5만원을 가지고 있다.  
```  