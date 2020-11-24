# Numpy 응용   
## 선형대수 연산    

```python  
# 행렬 내적 : np.dot(A, B)  
import numpy as np  
array1 = np.array([[1,2,3,4],[5,6,7,8]])  
array2 = np.array([[9,10],[11,12],[13,14],[15,16]])  

# 1*9 + 2*11 + 3*13 + 4*15 = 130  
# 1*10 + 2*12 + 3*14 + 4*16 = 140  
# 5*9 + 6*11 + 7*13 + 8*15 = 322  
# 5*10 + 6*12 + 7*14 + 8*16  = 348  

dot_output = np.dot(array1, array2)  
print(dot_output)    

Output  
[[130 140]  
 [322 348]]  

# 전치 행렬 : np.transpose(A)  
import numpy as np  
array1 = np.array([[1,2,3,4],[5,6,7,8]])  

transpose_output = np.transpose(array1)  
print(transpose_output)  

Output  
[[1 5]  
 [2 6]  
 [3 7]  
 [4 8]]  
```  
## 벡터화 연산  
- 벡터의 같은 인덱스에 위치한 데이터끼리 loop문 없이 연산을 수행  
- 연산 후 ndarray로 반환  

```python  
# 벡터화 연산  
import numpy as np  
array1 = np.array([1,2,3,4,5,6,7,8])  
print(array1)  
vector_array1 = array1 * 2 + 1  
print(type(vector_array1),vector_array1)  

Output  
[1 2 3 4 5 6 7 8]  
<class 'numpy.ndarray'> [ 3  5  7  9 11 13 15 17]  

# 리스트 방식 for문 사용  
import numpy as np  
array1 = [1,2,3,4,5,6,7,8]  
print(array1)  
list_array1 = [ i * 2 + 1 for i in array1] //Comperhension 사용  
print(type(list_array1), list_array1)  

Output  
[1, 2, 3, 4, 5, 6, 7, 8]  
<class 'list'> [3, 5, 7, 9, 11, 13, 15, 17]  
```  

## list와 ndarray 계산 성능    
```python  
# list 연산  
import time  
list_size = 10000000  
array1 = list(range(list_size))  
array2 = list(range(list_size))  
array3 = list(range(list_size))  

startTime = time.time()  
for i in range(len(array1)) :  
    array3[i] = array1[i]+array2[i]  
    
print("Time : ", time.time() - startTime)  

Output  
Time :  3.6067121028900146  
```  

```python  
# 벡터화 연산  
import numpy as np  
import time  
ndarray_size = 10000000  
array1 = np.arange(ndarray_size)  
array2 = np.arange(ndarray_size)  

startTime = time.time()  
array3 = array1 + array2  
print("Time : ", time.time() - startTime)  

Output  
Time :  0.19399809837341309  
```  

```python  
# 벡터화 연산 X 
import numpy as np  
import time  
ndarray_size = 10000000  
array1 = np.arange(ndarray_size)  
array2 = np.arange(ndarray_size)  

startTime = time.time()  
array3 = array1 + array2  
print("Time : ", time.time() - startTime)  

Output  
Time :  8.760003089904785   
```  
