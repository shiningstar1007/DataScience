# Python 함수, 모듈  

- 함수(Function) : 특정한 일을 할 수 있도록 미리 정의  
- 메서드(Method) : 함수와 비슷하지만 객체 내에 정의되어 있어서 맴버 함수라고 한다.  
- 함수와 메서드의 차이점은 함수는 단독으로 호출이 가능하지만 메서드는 객체를 통해서 호출해야 한다.  

## 함수 선언  
- def 함수명 콜론(:) 으로 작성하고 함수 내에서 실행할 문장은 다음 줄에서 들여쓰기를 통해서 작성한다.  
- 들여쓰기를 계속 해서 함수를 정의하며, 함수의 맨 마지막까지 들여쓰기로 작성을 한다.  
- 리턴할 값이 있으면 마지막에 return 을 해주면 된다.  

```python  
# 함수 선언  
def fruitShop(fruitNumber):  
    retPrice = 0  
    
    if fruitNumber == 1 :  
        print("사과 구입 완료!")  
        retPrice = 1000  
    elif fruitNumber == 2 :  
        print("배 구입 완료!")  
        retPrice = 2000  
    elif fruitNumber == 3 :  
        print("바나나 구입 완료!")  
        retPrice = 3000  
    else :  
        print("없는 과일 입니다.")  
    
    return retPrice  

# 메인 코드  
print("1 : 사과, 2 : 배, 3 : 바나나")  
fruit = int(input("어떤 과일을 구매하나요? "))  
print()  
price = fruitShop(fruit)  
print("지불 금액은 %d 입니다." % price)      

Output  
1 : 사과, 2 : 배, 3 : 바나나  
어떤 과일을 구매하나요? 1  

사과 구입 완료!  
지불 금액은 1000 입니다.  
```  

## 지역변수와 전역변수  
- 지역변수 : 함수(메소드 포함) 내에서만 사용된다. (한정적으로 접근 가능)  
- 전역변수 : 프로그램 전체에서 사용된다. (어디서든 접근 가능)  
- 지역변수와 전역변수의 명이 같으면 사용되는 위치에 따라 우선순위가 부여된다.  
- 함수(메소드 포함) 내에서는 지역변수가 우선적으로 사용된다.  
- 함수(메소드 포함) 내에서 전역변수를 사용하고 싶으면 global 예약어를 사용한다.  

```python  
# 전역 변수  
testValue = 20  

def testFunc1() :  
    # 지역 변수  
    testValue = 10  
    
    print("[testFunc1]testValue : %d" % testValue)  

def testFunc2() :  
    # 전역 변수 사용하도록 global 예약어 사용  
    global testValue  
    testValue = 10  
    print("[testFunc2]testValue : %d" % testValue)      
    
# 메인 코드  
testFunc1()  
print("[main]testValue : %d" %testValue)  
testFunc2()  
print("[main]testValue : %d" %testValue)  

Output  
[testFunc1]testValue : 10  
[main]testValue : 20  
[testFunc2]testValue : 10  
[main]testValue : 10  
```  

## pass 예약어  
- 함수를 정의하고 기능을 작성하지 않을 때 pass 예약어를 사용  
- 비워두면 에러가 나기 때문에 사용함  

```python  
def testFunc() :  
    pass  
```  

## 매개변수에 기본값을 설정해 놓고 전달하는 방법  
- 맨 마지막 매개변수 값은 default로 설정할 수 있다.  

```python  
def testFunc(param1, param2 = 0) :  
    retSum = param1 + param2  
    return retSum  

hap = 0  

hap = testFunc(20)  
print("매개변수 1개일 때의 합 : %d" % hap)  
hap = testFunc(20,30)  
print("매개변수 2개일 때의 합 : %d" % hap)  

Output  
매개변수 1개일 때의 합 : 20  
매개변수 2개일 때의 합 : 50  
```  

# 모듈  
- 표준 모듈, 사용자 정의 모듈, 서드파티(3rd party) 모듈로 구분한다.  
- 모듈은 함수의 집합이다.  
- 표준 모듈은 파이썬에서 제공하는 모듈이다.  
- 사용자 정의 모듈은 말 그대로 사용자가 직접 만들어서 사용하는 모듈이다.  
- 서드파티 모듈은 외부 회사나 단체에서 제공하는 모듈이다.  

```python  
# 파이썬에서 제공하는 표준 모듈의 목록 확인 할 때  
import sys  
print(sys.builtin_module_names)  

# 모듈과 예약어 확인 할 때  
dir(__builtins__)   
```  

## 모듈 사용 방법  
```python  
# testModule.py  
## 함수 선언  

def testFunc1() :  
    print("testFunc1")  

def testFunc2() :  
    print("testFunc2") 

# testMain.py  
## 모듈 추가  
import testModule  

## 메인 코드  
testModule.testFunc1()  
testModule.testFunc2()  

Output  
testFunc1  
testFunc2  
```  

## 모듈명을 생략하고 함수명을 사용하고 싶을 때  
```python  
# 특정 함수들만 사용할 때  
# from 모듈명 import 함수명,함수명 (1행 형식으로 작성한다.)  
from testModule import testFunc  

# 모든 함수를 사용할 때  
# from 모듈명 import *  
from testModule import *  

## 메인 코드  
testFunc1()  

Output  
testFunc1  
```  

# 함수 호출 시 매개변수의 전달 방식  
## Call By Value  
- 매개변수에 값을 전달하면 매개변수에 새로운 메모리가 할당되어 전달 받은 값을 저장한다.  
- 따라서 매개변수에 전달한 값은 변하지 않는다.  

```python  
def callByValue(param1) :  
    param1 = 100  

data = 10  
callByValue(data)  
print(data)  

Output  
10  
```  

## Call By Reference  
- 매개변수에 주소가 전달되어 매개변수도 전달 받은 주소를 참조하게 되어 같은 메모리 공간을 공유한다.  
- 보통 리스트(List), 튜플(Tuple), 딕셔너리(Dictionary), 세트(Set) 를 매개변수에 전달한다.  
- 따라서 매개변수를 함수 내에서 조작하면 동일한 메모리 공간을 사용하기에 데이터가 변경된다.  

```python  
def callByReference(param1) :  
    param1[0] = 100  

dataList = [1,2,3]  
callByReference(dataList)  
print(dataList)  

Output  
[100, 2, 3]  
```   