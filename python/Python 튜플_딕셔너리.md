# Python 튜플, 딕셔너리  

## 튜플(Tuple)  
- 리스트는 대괄호[]를 사용하여 생성하지만, 튜플은 소괄호()를 사용하여 생성한다.  
- 튜플은 초기 값을 설정하면 이 후 값을 수정할 수 없으며, 읽기만 가능하다.  
- 튜플 생성 시 소괄호()를 생략할 수도 있으며, 그런 경우에는 쉼표(,)를 붙여야 한다.  
- 튜플 전체를 삭제하는건 가능하다. (del 함수를 사용)  
- 튜플 사용 방법은 리스트와 동일하다.  

```python  
testTuple = (1,2,3)  
print(testTuple)  

Output  
(1, 2, 3)  

# 소괄호 생략  
testTuple = 1,2,3  
print(testTuple)  

Output  
(1,2,3)  
```  

- 튜플에 있는 데이터를 수정해야 할 경우에는 리스트로 변환하여 수정할 수 있다.  
- 리스트를 튜플로 변환할 수도 있다.  
```python  
testTuple = (1,2,3)  
print(testTuple)  
testList = list(testTuple)    // 튜플을 리스트로 변환  
testList[0:3] = [4,5,6]  
testTuple= tuple(testList)  //리스트를 튜플로 변환  
print(testTuple)  

Output  
(1, 2, 3)  
(4, 5, 6)  
```  

## 딕셔너리(Dictionary)  
- 중괄호 {}로 묶어서 구성한다.  
- 키(Key)와 값(Value)의 쌍으로 구성되어 있다.  
- 키:값 형태로 두 값을 연결해서 구성한다.  
- 딕셔너리에는 순서가 없어 생성한 순서대로 딕셔너리가 구성되어 있지 않을수도 있다.  
- 딕셔너리 내 데이터를 찾을 때 키(Key)를 가지고 찾는다.  
```python  
# 데이터 찾기  
TestDictionary = { '사과':1000, '배':2000, '바나나':3000 }  
print(TestDictionary['배'])  

Output  
2000  

# get 함수를 사용해서 데이터 찾기   
# get 함수를 사용해서 찾는게 안전함 (찾는 키가 없으면 아무것도 리턴 안함)  
TestDictionary = { '사과':1000, '배':2000, '바나나':3000 }  
print(TestDictionary.get('배'))  

Output  
2000  

# 데이터 추가  
TestDictionary = { '사과':1000 }  
TestDictionary['배'] = 3000   
print(TestDictionary['배'])  

Output  
3000  

# 데이터 삭제  
TestDictionary = { '사과':1000, '배':2000, '바나나':3000 }  
del(TestDictionary['배'])  
print(TestDictionary)  

Output  
{'사과': 1000, '바나나': 3000}  

# 데이터 수정  
TestDictionary = { '사과':1000, '배':2000, '바나나':3000 }  
TestDictionary['배'] = 5000  
print(TestDictionary['배'] )  

Output  
5000  
```  

## 세트(Set)  
- 키만 모아 놓은 딕셔너리의 특수현 형태이다.  
- 생성 할 때 딕셔너리와 비슷하게 중괄호{}를 사용하지만 키(Key)만 추가한다.  
- 키(Key)는 유일성임으로 중복되는 키는 자동으로 1개로 통합된다.  
```Python  
testSet = {'사과','배','바나나','배','귤'}  
print(testSet)  

Output  
{'귤', '바나나', '사과', '배'}  
```  

- 세트(Set)를 가지고 교집합, 합집합, 차집합, 대칭 차집합을 구할 수 있다.   

| <center>설명</center> | <center>기호</center> | <center>함수</center>    
|:--------:|:--------:|:--------:|      
|**<center>교집합</center>** |  <center> & </center> | <center>intersection</center> |   
|**<center>합집합</center>** |  <center> \| </center> | <center>union</center> |   
|**<center>차집합</center>** |  <center> - </center> | <center>difference</center> |   
|**<center>대칭 차집합</center>** |  <center> ^ </center> | <center>symmetric_difference</center> |   

```Python  
# 기호를 사용한 출력  
testSet1 = {'사과','배','바나나'}  
testSet2 = {'감','배','귤'}  
print(testSet1 & testSet2)  
print(testSet1 | testSet2)  
print(testSet1 - testSet2)  
print(testSet1 ^ testSet2)  

Output  
{'배'}  
{'바나나', '사과', '감', '귤', '배'}  
{'바나나', '사과'}  
{'바나나', '감', '사과', '귤'}  

# 함수를 사용한 출력  
testSet1 = {'사과','배','바나나'}  
testSet2 = {'감','배','귤'}  
print(testSet1.intersection(testSet2))  
print(testSet1.union(testSet2))  
print(testSet1.difference(testSet2))  
print(testSet1.symmetric_difference(testSet2))  

Output  
{'배'}  
{'바나나', '사과', '감', '귤', '배'}  
{'바나나', '사과'}  
{'바나나', '감', '사과', '귤'}  
```  






