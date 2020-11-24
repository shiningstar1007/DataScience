# Numpy (Numerical Python)  

## Numpy 장점  
- Python 대표 선형대수 라이브러리  
- 수치 해석을 할 때 많이 사용 됨  
- NumPy 기본적인 데이터 타입/객체는 ndarray(or array) : NumPy 기본 객체, N 차원 배열  
- Python 에서 선형대수 기반의 프로그램을 쉽게 만들 수 있도록 지원  
- 반복문을 사용하지 않고 대량 데이터의 배열 연산이 가능  
- 빠른 배열 연산 속도를 보장함  
- 대량 데이터 기반의 과학과 공학 프로그램은 빠른 계산 능력이 매우 중요  
- Python 기반의 많은 과학과 공학 패키지는 NumPy에 의존  
- C/C++과 같은 저수준 언어 기반의 호환 API를 제공  
- 배열 기반의 연산은과 다양한 데이터 핸들링 기능을 제공  

## NumPy 단점  
- Python의 대표적인 데이터 처리 패키지인 Pandas의 편리성에는 미치지 못함  
- 매우 방대한 기능을 지원하고 있기에 이를 다 배우기에는 상당한 시간과 코딩 경험이 필요함  

## NumPy 사용방법 : import numpy as np  
- 기본적으로 numpy의 줄인 np로 선언해서 사용함  

## NumPy 기반 데이터 타입 : ndarray  
- ndarray는 같은 종류의 데이터를 담을 수 있는 포괄적인 다차원 배열로 모든 데이터는 같은 자료형이어야 함  
- ndarray를 이용해 NumPy에서 다차원(Multi-dimension)배열을 쉽게 생성하고 다양한 연산 수행 가능  

## NumPy array() 함수  
- Python의 리스트와 같은 다양한 인자를 입력받아 ndarray로 변환 기능 수행  
- Numpy 모듈의 array() 함수를 이용하여 ndarray 생성  
- 인자는 파이썬 list 또는 ndarray 입력   

## ndarray 생성  
```python  
# 1차원 배열  
# 타입을 출력해보면 ndarray로 출력되며 콤마(,)가 붙지 않고 출력된다. (리스트하고 다름)  
import numpy as np  
array1 = np.array([1,3,5,7])  
print(array1)  
print(type(array1))  

Output  
[1 3 5 7]  
<class 'numpy.ndarray'>  

# 2차원 배열  
import numpy as np  
array2 = np.array([[1,3,5,7], [2,4,6,8]])  
print(array2)  

Output  
[[1 3 5 7]  
 [2 4 6 8]]  

# 3차원 배열  
import numpy as np  
array3 = np.array( [[[1,3,5,7], [2,4,6,8]], [[11,13,15,17], [12,14,16,18]]] )  
print(array3)  

Output  
[[[ 1  3  5  7]  
  [ 2  4  6  8]]  

 [[11 13 15 17]  
  [12 14 16 18]]]  
```  

## NumPy ndarray 데이터 타입/객체  
|  <center>타입</center> |  <center>설명</center> |     
|:--------:|:--------:|    
|**<center>ndarray.ndim</center>** | <center>차원개수(예, 2)</center> |    
|**<center>ndarray.shape</center>** | <center>배열크기(예, 3x5 메트릭스: (3, 5))</center> |    
|**<center>ndarray.size</center>** | <center>배열의원소개수(예, 15)</center> |    
|**<center>ndarray.itemsize</center>** | <center>원소의바이트크기(예: 8 byte)</center> |    
|**<center>ndarray.dtype</center>** | <center>배열의데이터타입(예: np.int64)</center> |    
|**<center>ndarray.data</center>** | <center>배열의데이터</center> |    

## ndarray 형태와 차원  
```python  
# ndarray 형태는 ndarray.shape 속성  
# ndarray 차원은 ndarray.ndim 속성  

# 1차원 배열  
import numpy as np  
array1 = np.array([1,3,5,7])  
print(array1)  
print(array1.ndim)  
print(array1.shape)  

Output  
[1 3 5 7]  
1 <- 1차원  
(4,) <- 튜플 형태로 전달되며, 요소 출력 후 뒤에 콤마(,)가 붙으며 출력  

# 2차원 배열  
import numpy as np  
array2 = np.array([[1,3,5,7], [2,4,6,8]])  
print(array2)  
print(array2.ndim)  
print(array2.shape)  

Output  
[[1 3 5 7]  
 [2 4 6 8]]  
2      <- 2차원  
(2, 4) <- 4개의 요소가 들어있는게 2개 있다.  

# 3차원 배열  
import numpy as np  
array3 = np.array( [[[1,3,5,7], [2,4,6,8]], [[11,13,15,17], [12,14,16,18]]] )  
print(array3)  
print(array3.ndim)  
print(array3.shape)  

Output  
[[[ 1  3  5  7]  
  [ 2  4  6  8]]  

 [[11 13 15 17]  
  [12 14 16 18]]]  
3        <- 3차원  
(2, 2, 4) <- 4개의 요소가 들어있는게 2개가 있으며 이게 2개가 있다.  
```

## ndarray 타입(type)  
- ndarray내의 데이터 타입은 연산의 특성상 같은 데이터 타입만 가능  
- 타입 옆에 써있는 숫자는 단일 값을 메모리에 저장하는데 필요한 bit수 (1bypte는 8bit를 의미)  

|  <center>데이터 형태</center> |  <center>타입</center> | <center>코드</center> |       
|:--------:|:--------:|:--------:|   
|**<center>bool 형</center>** | <center>bool</center> | <center> ? </center> |    
|**<center>int 형</center>** | <center>int8, int16, int32, int64</center> | <center>i1, i2, i4, i8</center> |    
|**<center>unsigned int형</center>** | <center>uint8, uint16, uint32, uint64</center> | <center>u1, u2, u4, u8</center> |    
|**<center>float 형</center>** | <center>float16, float32, float64</center> | <center>f2, f4, f8</center> |    
|**<center>complex 형</center>** | <center>complex64, complex128, complex256</center> | <center>c8, c16, c32</center> |    
|**<center>string 형</center>** | <center>string_</center> | <center>S</center> |    
|**<center>unicode 형</center>** | <center>unicode_</center> | <center>U</center> |    

### ndarray내의 데이터 타입은 ndarray.dtype  
```python  
# 정수  
import numpy as np  
array1 = np.array([1,3,5,7])  
print(array1)  
print(array1.dtype)  

Output  
[1 3 5 7]  
int32  

# 실수  
import numpy as np  
array1 = np.array([1.1, 2.2, 3.3, 4.4])  
print(array1)  
print(array1.dtype)  

Output  
[1.1 2.2 3.3 4.4]  
float64  
```  

### ndarray 생성 시 타입 지정  
```python  
# 데이터 코드를 이용한 타입 지정  
import numpy as np  
array1 = np.array([1,3,5,7], dtype='i1')  
print(array1)  
print(array1.dtype)  

Output  
[1 3 5 7]  
int8  

# 데이터 타입을 이용한 타입 지정  
import numpy as np  
array1 = np.array([1.1, 2.2, 3.3, 4.4], dtype=np.float16)  
print(array1)  
print(array1.dtype)  

Output  
[1.1 2.2 3.3 4.4]  
float16  
```  

## ndarray 타입(type) 변환 : astype()  
- 변경을 원하는 타입을 astype()의 인자로 입력  
- 대용량 데이터를 ndarray로 생성시 메모리를 절약하기 위해 사용  

```python  
# float64형 데이터를 int32로 변환  
ndarray_float64 = np.array([1.1, 2.2, 3.3, 4.4])  
print(ndarray_float64, ndarray_float64.dtype)  
ndarray_int32 = ndarray_float64.astype('int32')  
print(ndarray_int32, ndarray_int32.dtype)  

Output  
[1.1 2.2 3.3 4.4] float64  
[1 2 3 4] int32  
```  

## ndarray - axis  
- ndarray의 shape는 axis0, axis1, axis2에 의해 결정  
- 1차원의 경우는 axis0, 2차원은 axis0, axis1, 3차원은 axis0, axis1, axis2 ...  
- 예를 들어 3차원 shape가 (2, 3, 4) 인 경우, axis0은 2, axis1은 3, axis2는 4의 값을 가지고 있다.  

### ndarray에서 aixs 기반의 연산함수 수행  
```python  
# 2차원 배열  
import numpy as np  
array3 = np.array( [[1,3,5,7], [2,4,6,8]] )  
print("axis0 =", array3.sum(axis=0)) //axis 0 기준으로 더하기  
print("axis1 =", array3.sum(axis=1)) //axis 1 기준으로 더하기  
print("sum = %d" % array3.sum())  

Output  
axis0 = [ 3  7 11 15]  
axis1 = [16 20]  
sum = 36  
```  

## ndarray - 편리한 생성 : arange, zeros, ones  
- arange() : 연속값을 요소로 가지는 ndarray 생성  
- zeros() : 0으로 초기화 된 ndarray 생성  
- ones() : 1로 초기화 된 ndarray 생성  

```python  
# arange()  
import numpy as np  
array1 = np.arange(5) // 0부터 4까지 1씩 증가해서 5개를 생성  
print(array1, array1.dtype, array1.shape)  

Output  
[0 1 2 3 4] int32 (5,)  

# zeros()  
import numpy as np  
array2 = np.zeros((2,3), dtype=np.int32) // 2차원 ndarray 생성  
print(array2, array2.dtype, array2.shape)  

Output  
[[0 0 0]  
 [0 0 0]] int32 (2, 3)  

# ones()  
import numpy as np  
array3 = np.ones((2, 3, 4))  // 3차원 ndarray 생성 타입 안주면 기본 float64  
print(array3, array3.dtype, array3.shape)  

Output  
[[[1. 1. 1. 1.]  
  [1. 1. 1. 1.]  
  [1. 1. 1. 1.]]  

 [[1. 1. 1. 1.]  
  [1. 1. 1. 1.]  
  [1. 1. 1. 1.]]] float64 (2, 3, 4)  
```

## ndarray - 차원과 크기 변경 : reshape()  
- 변환 형태를 함수 인자로 입력  

```python  
# 1차원을 2차원 3차원으로 변환  
import numpy as np   
array1 = np.array([1,2,3,4,5,6,7,8])  
print(array1)  

array2 = array1.reshape(2, 4) // 2차원의 2X5 ndarray로 변환  
print(array2)  

array3 = array1.reshape(2, 2, 2) // 3차원의 2X2X2 ndarray로 변환  
print(array3)  

Output  
[1 2 3 4 5 6 7 8]  
[[1 2 3 4]  
 [5 6 7 8]]  
[[[1 2]  
  [3 4]]  

 [[5 6]  
  [7 8]]]  
  
# 인자값에 -1을 넣으면 자동으로 계산하여 reshape  
# 인자값에 -1은 하나만 넣어야 함  
import numpy as np   
array1 = np.array([1,2,3,4,5,6,7,8,9,10])  
print(array1)  

array2 = array1.reshape(-1, 2) //axis1이 2개인 크기에 맞춰 axis0을 자동으로 계산  
print(array2)  

array2 = array1.reshape(2, -1) //axis0이 2개인 크기에 맞춰 axis1을 자동으로 계산  
print(array2)  

Output  
[ 1  2  3  4  5  6  7  8  9 10]  
[[ 1  2]  
 [ 3  4]  
 [ 5  6]  
 [ 7  8]  
 [ 9 10]]  
[[ 1  2  3  4  5]  
 [ 6  7  8  9 10]]  

# 2차원을 1차원으로 변환  
import numpy as np   
array2 = np.array([[1,2,3,4],[5,6,7,8]])  
print(array2)  

array1 = array2.reshape(-1,)   

Output  
[[1 2 3 4]  
 [5 6 7 8]]  
[1 2 3 4 5 6 7 8]  
```  