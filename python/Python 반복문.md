# 반복문

## for 문 기본 형식  
- for문은 반복할 횟수를 range() 함수에서 지정하면, 그 횟수만큼 반복을 한다.  
- for문을 작성 할 때도 마찬가지로 들여쓰기를 잘 해야 한다.  
- for문 작성 방법은 아래와 같다.  
```Python  
for 변수 in range(초기값, 종료값, 증가값) :  
    반복 문 실행  
```  

range()를 사용 할 때 range(초기값, 종료값, 증가값) 말고 range(값)만 주면   
0부터 주어진 값까지 1씩 증가하는 문장과 같다.  

```Python   
# range(초기값, 종료값, 증가값) 반복 후 for문 종료  
for value in range(0, 2, 1) :  
   print("for문 반복 %d 회차" % (value + 1))  

Output  
for문 반복 1회차  
for문 반복 2회차  
```  

```Python  
# range(값) 반복 후 for문 종료  
for value in range(2) :  
   print("for문 반복 %d 회차" % (value + 1))  

Output  
for문 반복 1회차  
for문 반복 2회차  
```  

## index가 존재하는 문자열 또는 list의 for문을 활용한 출력방법  
- 문자열을 for문을 이용하여 순회하면 1글자씩 접근 가능   
- list를 for문을 이용하여 순회하면 1개씩 접근 가능   
- 정수,소수는 불가능, 즉 index가 존재하는거만 가능   

```python  
# 문자열 순회
data = 'hello python'
for value in data:
    print(value, end=' ')

Output
h e l l o   p y t h o n 

# list 순회
data = [10,20,30,40,50]
for value in data:
    print(value, end=' ')

Output
10 20 30 40 50 
```  

## dictionary의 for문을 활용한 출력방법   
- dictionary를 순회 하게 되면 기본적으로 key값을 참조한다.   
- keys() 함수를 이용하여 key 값만 순회 할 수 있다.   
- values() 함수를 이용하여 value 값만 순회 할 수 있다.   
- items() 함수를 이용하면 tuple 형태로 반환 되기 때문에 key, value 순회가 가능하다.   

```python  
# 기본적으로 순회 할 때
dic_list = {'apple' : 2000, 'orange' : 3000, 'banana' : 4000}
for key in dic_list:
    print(key)

Output
apple
orange
banana

# keys() 함수로 순회 할 때
dic_list = {'apple' : 2000, 'orange' : 3000, 'banana' : 4000}
for key in dic_list.keys():
    print(key)

Output
apple
orange
banana

# values() 함수로 순회 할 때
dic_list = {'apple' : 2000, 'orange' : 3000, 'banana' : 4000}
for key in dic_list.values():
    print(key)

Output
2000
3000
4000

# items() 함수로 순회 할 때
dic_list = {'apple' : 2000, 'orange' : 3000, 'banana' : 4000}
for key, value in dic_list.items():
    print(key, value)

Output
apple 2000
orange 3000
banana 4000
```  

## for에서 index 사용하기  
- 리스트를 순회 할 때 값만 추출함 (enumerate 함수 사용)  

```python  
data = [10,20,30,40,50]

for index, num in enumerate(data):
    print(index, num)

Output
0 10
1 20
2 30
3 40
4 50
```  

## while 문 기본형식  
- while문은 for문 처럼 반복 횟수를 결정하는 것과 다르게 조건식이 참이면 반복한다.  
- while문은 작성 할 때도 마찬가지로 들여쓰기를 잘 해야 한다.  
- while문 작성 방법은 아래와 같다.  
```Python  
while 조건식 :  
    반복 문 실행  
```  

```Python   
# 2회 반복 후 while문 종료  
value = 0  
while value < 2 :  
    print("while문 반복 %d 회차" % (value + 1))  
    value += 1  

Output  
while문 반복 1회차  
while문 반복 2회차  
```  

### while 문 무한루프  
- while문 조건식이 True인 경우에는 끝나지 않고 무한으로 반복한다.  
```Python   
# 무한 루프  
value = 0  
while True :  
    value += 1  
    print("while문 반복 %d 회차" % value)  

Output  
while문 반복 1회차  
~ 무한 반복  
```  

- while문 무한 루프를 종료 시키는 방법은 break문을 사용한다.  
```Python   
# 무한 루프에서 value 값이 정수 2면 종료 시키는 break문  
value = 0  
while True :  
    value += 1  
    print("while문 반복 %d 회차" % value)  
    if value == 2 :  
        break   

Output  
while문 반복 1회차  
while문 반복 2회차  
```  

- while문 무한 루프내 특정 조건에 대해서는 반복문 처음으로 돌아가게 하기 위해서는 continue문을 사용한다.  
```Python  
# 무한 루프에서 value 값이 정수 2면 건너 뛰는 continue문  
value = 0  
while True :  
    value += 1  
    if value == 2 :  
        continue   

    print("while문 반복 %d 회차" % value)  
    if value == 3 :  
        break   

Output  
while문 반복 1회차  
while문 반복 3회차  
```  

## print() 함수를 사용하여 출력시 Tip   

### end=""    
- end=""를 사용하여 print 문을 이용해 출력을 완료한 뒤의 내용을 수정할 수 있다.  
- 기본 값으로는 개행(\n)이 들어가 있으며 이를 사용해 개행을 없에거나 원하는 문자를 입력할 수 있다.   
- 개행은 줄바꿈이라고 생각하면 됨  
- 사용 방법은 print문 작성 후 퍼센트(%)가 아닌 콤마(,) 를 작성 후 end="" 를 작성하면 된다.   
  
```Python    
for value in range(3) :    
    print("출력중", end=" ")    

Output  
출력중 출력중 출력중   
```    

### sep=""   
- sep=""를 사용하여 print 문을 이용해 출력문 사이에 내용을 넣을 수 있다.  
- 기본 값으로는 공백이 들어가 있으며 이를 사용해 원하는 문자를 삽입할 수 있다.  
- 사용 방법은 print문 작성 후 퍼센트(%)가 아닌 콤마(,) 를 작성 후 sep="" 를 작성하면 된다.  
  
```Python    
print("출력중","출력중","출력중", sep="*sep*")   

Output  
출력중*sep*출력중*sep*출력중  
```  