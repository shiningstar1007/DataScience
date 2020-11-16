# Python 리스트

## 리스트와 배열의 차이점  
- 기존 C/C++ 같은 언어에서는 같은 데이터형만 묶어서 사용하는 배열이라는 개념이 있다.  
- 리스트는 정수,문자열,실수 등 서로 다른 데이터형을 하나로 묶을 수 있다.  
- 따라서 리스트와 배열의 큰 차이점은 서로 다른 데이터형을 하나로 묶어서 사용할 수 있다.  

## 리스트 생성 방법  
```python  
리스트명 = [값,값,값,값] // 리스트 생성 및 초기화  
testList = [0,1,2,3]  
for i in range(4) :  
    print("값:%d" % testList[i] , end=" ")   

Output  
값:0 값:1 값:2 값:3   

append() 함수  
testList = [] // 빈 리스트 생성  
testList.append(0) // 정수형 0 추가  
testList.append(1)  
testList.append(2)   
testList.append(3)  
for i in range(4) :  
    print("값:%d" % testList[i] , end=" ")    

Output  
값:0 값:1 값:2 값:3   
```  

## 리스트 값에 접근하는 방법  
```python  
# 음수값으로 접근  
# 아래 리스트의 총 개수는 4개이므로 -4까지 접근이 가능함  
# 리스트의 총 개수를 넘어가면 오류가 발생함  
# -4는 리스트의 맨 앞부분이며, -1은 리스트의 맨 뒷부분   

testList = [0,1,2,3]  
print("testList[-1]은 %d, testList[-4]는 %d" % (testList[-1], testList[-4]))  

Output  
testList[-1]은 3, testList[-4]는 0   

# 콜론(:)을 사용해서 범위 지정  
# 몇번째 위치부터 몇개를 사용할지 지정  
# 0:2 는 리스트의 0번째 위치부터 2개를 사용  

testList = [0,1,2,3]  
print(testList[0:2])  

Output  
[0, 1]  

# 콜론(:)을 사용해서 앞이나 뒤를 생략  
testList = [0,1,2,3]  
print(testList[1:])  
print(testList[:2])  

Output  
[1, 2, 3]  
[0, 1]  

# 리스트의 항목 건너뛰며 접근  
# 콜론(:)을 2개 사용해서 몇번 건너 뛰며 접근할지 지정  
# ::2는 리스트 접근 시 2번째는 건너 뛰며 접근  
# ::-2 는 역순으로 리스트 접근 시 2번째는 건너 뛰며 접근  
testList = [1,2,3,4,5,6,7,8]  
print(testList[::2])  
print(testList[::-2])  

Output  
[1, 3, 5, 7]  
[8, 6, 4, 2]  
```   

## 리스트끼리 연산  
```python  
# 리스트끼리 합치기  
testList1 = [1,2,3,4]  
testList2 = [5,6,7,8]  

testList1 = testList1 + testList2  
print(testList1)  

Output  
[1, 2, 3, 4, 5, 6, 7, 8]  

# 리스트를 정수 만큼 곱하여 늘리기  
testList1 = [1,2,3,4]  
testList1 = testList1 * 2  
print(testList1)  

Output  
[1, 2, 3, 4, 1, 2, 3, 4]  
```  

## 리스트 값 변경  
- C/C++에서 배열에 접근하듯이 해당 리스트의 데이터에 접근하며 데이터를 변경  
```python  
# 일반적인 리스트 데이터 변경   
testList1 = [0,0,0,0]  
print(testList1)  
testList1[1]=1  
testList1[2]=2  
testList1[3]=3  
print(testList1)  

Output  
[0, 0, 0, 0]  
[0, 1, 2, 3]  

# 범위 지정하여 리스트 데이터 변경  
# 콜론(:)을 사용해서 범위를 지정하고 값을 변경  
testList1 = [0,0,0,0]  
print(testList1)  
testList1[0:4] = [1,2,3,4]  
print(testList1)  

Output  
[0, 0, 0, 0]  
[1, 2, 3, 4]  
```  

## 리스트 데이터 삭제  
```python  
# del 함수를 사용  
testList1 = [1,2,3,4]  
print(testList1)  
del(testList1[1])  
print(testList1)  

Output  
[1, 2, 3, 4]  
[1, 3, 4]  

# 콜론(:)을 사용해서 범위를 지정하고 값을 삭제  
# n번째 시작부터 n번째까지 삭제  
testList1 = [1,2,3,4,5,6]  
print(testList1)  
testList1[1:3] = []  
print(testList1)  

Output  
[1, 2, 3, 4, 5, 6]  
[1, 4, 5, 6]  

# 리스트 자체를 삭제  
testList1 = [1,2,3,4,5,6]  
testList1 = [] // 값 전체가 삭제  
del(testList1) // testList1 자체가 삭제  
```  

## 컴프리헨션(Comperhension)  
- 값이 순차적인 리스트를 생성할 때 사용한다.  
- 리스트 = [수식 for 변수명 range() if 조건식]  
```python  
# 리스트 = [수식 for 변수명 range()]  
testList = []  
testList = [number for number in range(1, 3)]  
print(testList)  

Output    
[1, 2]  

# 리스트 = [수식 for 변수명 range() if 조건식]  
testList = []  
testList = [number for number in range(1, 9) if number % 2 == 0]  
print(testList)  

Output    
[2, 4, 6, 8]  
```   

## 리스트 복사  
```python    
# 얕은 복사(shallow copy)  
# 동일한 메모리 공간을 공유한다.  
oldList = ['사과','배','바나나']  
newList = oldList  
print(oldList)  
newList[1] = '귤'  
print(oldList)  

Output  
['사과', '배', '바나나']  
['사과', '귤', '바나나']  

# 깊은 복사(deep copy)  
# 데이터 전체를 복사해서 새로 만든다.  
oldList = ['사과','배','바나나']  
newList = oldList[:]  
print(oldList)  
newList[1] = '귤'  
print(oldList)  
print(newList)  

Output  
['사과', '배', '바나나']  
['사과', '배', '바나나']  
['사과', '귤', '바나나']  
```   

## 리스트 함수    
| <center>함수</center> | <center>설명</center>  
|:--------:|:--------:|      
|**<center>append(값)</center>** |  <center>맨 뒤에 값을 추가한다.</center> |   
|**<center>insert(위치,값)</center>** |  <center>지정된 위치에 값을 삽입한다.</center> |   
|**<center>remove(값)</center>** |  <center>지정된 위치의 값을 삭제한다.</center> |   
|**<center>pop()</center>** |  <center>맨 뒤에 값을 빼내고 리스트 항목에서 삭제한다.</center> |   
|**<center>clear()</center>** |  <center>모든 데이터를 초기화 한다.</center> |   
|**<center>del(값)</center>** |  <center>지정된 위치의 항목을 삭제한다.</center> |   
|**<center>sort()</center>** |  <center>항목을 정렬한다.</center> |   
|**<center>reverse()</center>** |  <center>항목을 역순으로 재정렬한다.</center> |   
|**<center>index(값)</center>** |  <center>지정한 값을 찾아 해당 위치를 반환한다.</center> |   
|**<center>extend(리스트)</center>** |  <center>리스트 뒤에 리스트를 추가한다.</center> |   
|**<center>count()</center>** |  <center>해당 값의 개수를 센다.</center> |   
|**<center>len(리스트)</center>** |  <center>리스트에 포함된 전체 항목의 개수를 센다.</center> |   
|**<center>copy()</center>** |  <center>리스트의 내용을 새로운 리스트에 복사한다.</center> |   
|**<center>sorted(리스트)</center>** |  <center>리스트의 항목을 정렬해서 새로운 리스트에 대입한다.</center> |   


## 2차원 리스트  
- 1차원 리스트를 여러개 연결한거  
- C/C++에서 2차원 배열과 비슷한 개념  
- 불규칙한 크기의 2차원 리스트도 생성 가능  
```python  
testList = [[1,2,3],[4],[5,6,7,8]]  
print(testList)  

Output  
[[1, 2, 3], [4], [5, 6, 7, 8]]  
```  