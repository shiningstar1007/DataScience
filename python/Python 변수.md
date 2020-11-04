# Python 변수

## 변수의 선언  
- 파이썬은 기존 C/C++, 자바 등등 기존에 변수를 선언 할 때 사용하는 데이터 형식(int,bool,char)이 없다.  
- 파이썬은 그냥 변수명을 선언하고 선언한 변수에 값을 넣으면 자동으로 데이터 형식이 정해진다.  
- 파이썬은 기존 C/C++, 자바 등등 기존에 변수를 선언해야 하는거와는 다르게  
선언을 할 필요는 없으나 미리 선언해서 사용하는 것이 좋다.  

```Python  
intVar = 0  
boolVar = True  
strVar =""  

이 변수들을 이렇게도 선언 할 수 있다  
intVar, boolVar, strVar = 0, True, ""  

해당 변수의 타입을 확인 할 땐 type 함수를 사용한다.  
```

## 변수명 규칙  
- 대/소문자를 구분한다. (myValue와 MyValue는 다른 변수)  
- 문자, 숫자, 언더바를 포함할 수 있다. (_myValue(o))  
- 숫자로 시작하는 변수는 선언 할 수 없다. (1MyValue(x))  
- 예약어는 변수명으로 사용할 수 없다.  
(True, False, None, and, or, not, break, continue, return, if, else, elif, for, while, try, except, finally, global, import 등등..)  


## 변수 사용시 주의해야 할 부분  
- 변수에 값을 넣으면 사용 가능하다. (기존 C/C++ 등에서 변수를 사용하듯이 사용하면 된다.)  
- 변수의 데이터 형식은 값을 넣는 순간마다 변경될 수 있는 유연한 구조이다.  
- 기존에 값이 있는 변수에 새로운 값을 넣으면 새로 입력한 값으로 변경된다.  
- 기존 intVar 변수에 있는 값이 정수 5가 있는 상태에서 True 값을 넣으면   
intVar 변수에 있던 정수 5는 사라지고 True 값이 저장 된다.  
즉 int형 변수에서 Boolean형 변수로 변경 된다.  

```Python
intVar = 5      # 정수형 변수가 생성  
type(intVar)    # <class 'int'> 출력  
intVar = True  # 이 순간에 정수형 변수에서 Boolean형 변수로 변경  
type(intVar)    # <class 'bool'> 출력  
```







