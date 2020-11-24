# ndarray - 인덱싱(indexing)    
- 인덱싱 유형  
  - 특정 위치의 인덱스 값을 지정하면 해당 위치의 데이터가 변환 (단일 값 추출)  
- 슬라이싱(Slicing)  
  - 연속된 인덱스상의 ndarray를 추출하는 방식  
  - ':' 기호 사이에 시작 인덱스와 종료 인덱스를 표시하면 시작 인덱스에서 종료 인덱스 -1 위치에 있는 ndarray를 반환  
  - 예를 들어 1:4 는 시작 인덱스 1과 종료 인덱스 3까지에 해당하는 ndarray를 반환  
- 펜시 인덱싱(Fancy Indexing)  
  - 일정한 인덱싱 집합을 리스트 또는 ndarray 형태로 지정해 해당 위치에 있는 ndarray를 반환  
- 불린 인덱싱(Boolean Indexing)  
  - 특정 조건에 해당 여부인 TRUE/FALSE값 인덱싱 집합을 기반으로 TRUE에 해당하는 인덱스 위치에 있는 ndarray를 반환  

### 단일값 추출 : 1차원 ndarray  
- ndarray는 axis를 기준으로 0부터 시작하는 위치 인덱스 값을 가지고 있음  
- 해당 인덱스 값을 []에 명시하여 단일 값을 추출  
- 마이너스가 인덱스로 사용되면 맨 뒤에서부터 위치를 지정  
- 예를들어 1번째 인덱스에 있는 값을 추출할 땐 array1[1]  
- 값을 수정할 땐 반대로 대입하면 됨  

```python  
import numpy as np  
array1 =np.array([1,3,5,7,9,11,13])  
print(array1)  
print("array1[2]:", array1[2])  
print("array1[-1]:", array1[-1])  

Output  
[ 1  3  5  7  9 11 13]  
array1[2]: 5  
array1[-1]: 13  
```   

### 단일값 추출 : 2차원 ndarray  
- 2차원 ndarray의 단일값을 추출 할 땐 [axis0값, axis1값] 지정하여 추출  

```python  
import numpy as np  
array2 = np.array([[1,2,3,4],[5,6,7,8]])  
print(array2)  
print("array2[0,0]:", array2[0,0])  
print("array2[1,-1]:", array2[1,-1])  

Output  
[[1 2 3 4]  
 [5 6 7 8]]  
array2[0,0]: 1  
array2[1,2]: 8  
```   

### 슬라이싱(Slicing) : 1차원 ndarray  
- ':' 을 이용하여 연속된 값을 선택  

```python  
import numpy as np  
array1 =np.array([1,3,5,7,9,11,13])  
print(array1)  
print("array1[0:2]:", array1[0:2])  

Output  
[ 1  3  5  7  9 11 13]  
[ 1  3  5  7  9 11 13]  
array1[0:2]: [1 3]  
```   

### 슬라이싱(Slicing) : 2차원 ndarray  
- ':' 을 이용하여 2차원 ndarray의 단일값을 추출 할 땐 [1차원 슬라이싱(axis0값), 1차원 슬라이싱(axis1값)] 지정하여 추출  

```python  
import numpy as np  
array2 = np.array([[1,2,3,4],[5,6,7,8],[9,10,11,12]])  
print(array2)  
print("array2[0:2, 0:2]:\n", array2[0:2, 0:2])  
print("array2[0:2, :]:\n", array2[0:2, :])  
print("array2[:, 0:1]:\n", array2[:, 0:1])  
print("array2[:, :]:\n", array2[:, :])  
print("array2[:2, 1:]:\n", array2[:2, 1:])  

Output  
[[ 1  2  3  4]  
 [ 5  6  7  8]  
 [ 9 10 11 12]]  
array2[0:2, 0:2]:  
 [[1 2]  
 [5 6]]  
array2[0:2, :]:  
 [[1 2 3 4]  
 [5 6 7 8]]  
array2[:, 0:1]:  
 [[1]  
 [5]  
 [9]]  
array2[:, :]:  
 [[ 1  2  3  4]  
 [ 5  6  7  8]  
 [ 9 10 11 12]]  
array2[:2, 1:]:  
 [[2 3 4]  
 [6 7 8]]  
```   

### 팬시 인덱싱(Fancy Indexing) : 1차원  
- 리스트나 ndarray로 인덱스 집합을 지정하면 해당 위치의 인덱스에 해당하는 ndarray를 반환  

```python  
import numpy as np  
array1 =np.array([1,3,5,7,9,11,13])  
print(array1)  
print("array1[[2,4,6]]:", array1[[2,4,6]])  

Output  
[ 1  3  5  7  9 11 13]  
array1[[2,4,6]]: [ 5  9 13]  
```   

### 팬시 인덱싱(Fancy Indexing) : 2차원  
- 단일 인덱싱 또는 슬라이싱 또는 팬시 인덱싱을 조합해서 사용 가능  

```python  
import numpy as np  
array2 = np.array([[1,2,3,4],[5,6,7,8],[9,10,11,12]])  
print(array2)  
print("array2[[0,1],[1,2]]:\n", array2[[0,1],[1,2]])  
print("array2[[0,1],1:2]:\n", array2[[0,1],1:2])  
print("array2[[0,1],3]:\n", array2[[0,1],3])  
print("array2[[0,1]]:\n", array2[[0,1]])  

Output  
[[ 1  2  3  4]  
 [ 5  6  7  8]  
 [ 9 10 11 12]]  
array2[[0,1],[1,2]]:  
 [2 7]  
array2[[0,1],1:2]:  
 [[2]  
 [6]]  
array2[[0,1],3]:  
 [4 8]  
array2[[0,1]]:  
 [[1 2 3 4]  
 [5 6 7 8]]  
```   

### 불린 인덱싱(Boolean indexing)  
- 조건 필터링과 검색을 동시에 가능한 인덱싱 방식  
- 먼저 조건을 []내에 입력하면 해당 조건의 FALSE 값은 무시하고 TRUE 값에 해당하는 Index 값만 저장  

```python  
# 1차원 ndarray 에서 짝수만 찾을 때  
import numpy as np  
array1 =np.array([1,3,2,5,7,6,8,4])  
print(array1)  
print(array1 % 2 == 0)  
print(array1[array1 % 2 == 0])  

Output  
[1 3 2 5 7 6 8 4]  
[False False True False False True True True]  
[2 6 8 4]  

# 2차원 ndarray 에서 짝수만 찾을 때  
import numpy as np  
array2 = np.array([[1,2,3,4],[5,6,7,8],[9,10,11,12]])  
print(array2)  
print(array2 % 2 == 0)  
print(array2[array2 % 2 == 0])  

Output  
[[ 1  2  3  4]  
 [ 5  6  7  8]  
 [ 9 10 11 12]]  
[[False  True False  True]  
 [False  True False  True]  
 [False  True False  True]]  
[ 2  4  6  8 10 12]  
```   
