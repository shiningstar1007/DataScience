# 배열의 정렬 - sort()와 argsort()    
- numpy.sort() : 원본 행렬은 그대로 두고 원본 행렬의 정렬된 행렬을 반환  
- numpy.argsort() : 원본 행렬은 그대로 두고 원본 행렬의 정렬된 인덱스를 ndarray로 반환  
- ndarray.sort() : 원본 행렬 자체를 정렬  

### 1차원 배열의 정렬  
```python  
# numpy.sort() 오름차순  
import numpy as np  
array1 =np.array([1,3,2,5,7,6,8,4])  
print("array1:", array1)  
np_sort_array = np.sort(array1)  
print("np_sort_array:", np_sort_array)  
print("array1:", array1)  

Output  
array1: [1 3 2 5 7 6 8 4]  
np_sort_array: [1 2 3 4 5 6 7 8]  
array1: [1 3 2 5 7 6 8 4]  
```  

```python  
# numpy.sort() 내림차순  
import numpy as np  
array1 =np.array([1,3,2,5,7,6,8,4])  
print("array1:", array1)  
np_sort_array = np.sort(array1)[::-1]  
print("np_sort_array:", np_sort_array)  
print("array1:", array1)  

Output  
array1: [1 3 2 5 7 6 8 4]
np_sort_array: [8 7 6 5 4 3 2 1]
array1: [1 3 2 5 7 6 8 4]
```  

```python  
# numpy.argsort()  
import numpy as np  
array1 =np.array([1,3,2,5,7,6,8,4])  
print("array1:", array1)  
retIndex = np.argsort(array1)  
print("retIndex:", retIndex)  
np_argsort_array = array1[retIndex]  
print("np_argsort_array:", np_argsort_array)  
print("array1:", array1)  

Output  
array1: [1 3 2 5 7 6 8 4]  
retIndex: [0 2 1 7 3 5 4 6]  
np_argsort_array: [1 2 3 4 5 6 7 8]  
array1: [1 3 2 5 7 6 8 4]  
```  

```python  
# ndarray.sort()  
import numpy as np  
array1 =np.array([1,3,2,5,7,6,8,4])  
print("array1:", array1)  
nd_sort_array = array1.sort()  
print("nd_sort_array:", nd_sort_array)  
print("array1:", array1)  

Output  
array1: [1 3 2 5 7 6 8 4]  
nd_sort_array: [1 2 3 4 5 6 7 8]  
array1: [1 2 3 4 5 6 7 8]  
```  

### 2차원 배열의 정렬  
- 2차원 배열에서 axis 기반으로 sort  
  - axis 방향으로 sort  

```python  
import numpy as np  
array2 = np.array([[8,6,7,5],[3,2,1,4],[9,12,11,10]])  
print("array2:\n", array2)  
np_sort_array_axis0 = np.sort(array2, axis=0)  
np_sort_array_axis1 = np.sort(array2, axis=1)  
print("np_sort_array_axis0 :\n", np_sort_array_axis0)  
print("np_sort_array_axis1 :\n", np_sort_array_axis1)  
print("array2:\n", array2)  

Output  
array2:  
 [[ 8  6  7  5]  
 [ 3  2  1  4]  
 [ 9 12 11 10]]  
np_sort_array_axis0 :  
 [[ 3  2  1  4]  
 [ 8  6  7  5]  
 [ 9 12 11 10]]  
np_sort_array_axis1 :  
 [[ 5  6  7  8]  
 [ 1  2  3  4]  
 [ 9 10 11 12]]  
array2:  
 [[ 8  6  7  5]  
 [ 3  2  1  4]  
 [ 9 12 11 10]]  
```   

### Key-Value 형태의 데이터를 정렬  
```python   
# 사과=100, 배=200, 딸기=150, 바나나=300, 귤=50   
import numpy as np  
fruit_array1 = np.array(["사과", "배", "딸기", "바나나", "귤"])  
price_array1 = np.array([100, 200, 150, 300, 50])  

sort_array_index = np.argsort(price_array1)  
print(sort_array_index)  
print(fruit_array1[sort_array_index])   
print(price_array1[sort_array_index])  

Output  
[4 0 2 1 3]  
['귤' '사과' '딸기' '배' '바나나']  
[ 50 100 150 200 300]  
```  
