# Class 와 Object  

## Class  
- 속성(Attribute)와 동작(Method)를 갖는 데이터 타입  
- Python에서 사용하는 string, int, list, dict 등 모든게 다 클래스로 존재 함  
- 다루고자 하는 데이터(변수)와 데이터를 다루는 연산(함수)를 하나로 캡슐화(encapsulation)  
- 모델링에서 중요시 하는 속성에 따라 클래스의 속성과 행동이 각각 달라짐  

```python
data = [1, 2, 3]
data.append(4) # append 라는 Method를 호출하여 Attribute 4를 추가
print(data)

Output
[1, 2, 3, 4]
```

### Class 선언  
- 객체를 생성하기 위해서 객체의 모체가 되는 Class를 미리 선언해야 함  

### 생성자 __init__(self)  
- 생성자, 클래스 인스턴스가 생성될 때 호출됨  
- self인자는 항상 첫번째에 오며 자기 자신을 가리킴  
- 이름이 꼭 self일 필요는 없지만, 기본적으로 self로 사용함  
- 생성자에서는 해당 클래스가 다루는 데이터를 정의  
  - 데이터를 멤머 변수(Member variable) 또는 속성(attribute)라고 함  

### self  
- 파이썬의 Method는 항상 첫번째 인자로 self를 전달  
- self는 현재 해당 Method가 호출되는 객체 자신을 가리킴  
- 위치는 항상 맨 처음의 parameter이며 기본적으로 self로 사용  

## Method 정의  
- 멤버함수라고도 하며, 해당 클래스의 Object에서만 호출가능하다.  
- 메서드는 객체 레벨에서 호출되며, 해당 객체의 속성에 대한 연산을 행함  
- {obj}.{method}() 형태  

### Method Type  
- instance Method - 객체로 호출  
  - 메서드는 객체 레벨로 호출되기 때문에 호출된 객체에만 영향을 미친다.  
- Class Method(Static Method) - Class로 호출  
  - Class 메서드의 경우, 클래스 레벨로 호출되기 때문에, 클래스 멤버 변수만 변경이 가능하다.  

```python

class testClass:
    def __init__(self): # 생성자
        self.name = 'test'
        self.nationality = 'python'
        
t1 = testClass() # Class 생성 시 생성자가 호출
print(t1.name, t1.nationality)

Output
test python

class testClass:
    def __init__(self, name, nationality): # 생성자
        self.name = name
        self.nationality = nationality
        
t1 = testClass('user', 'korea') # Class 생성 시 초기값 설정
print(t1.name, t1.nationality)

Output
user korea

class testClass:
    def __init__(self, name, nationality): # 생성자
        self.name = name
        self.nationality = nationality
        
    def printData(self): # Method printData 이므로 가장 맨 앞은 self 가 온다.
        print(self.name, self.nationality)
        
t1 = testClass('user', 'korea') # Class 생성 시 초기값 설정
t1.printData()

Output
user korean
```

### Method Type  
- instance Method - 객체로 호출  
  - 메서드는 객체 레벨로 호출되기 때문에 호출된 객체에만 영향을 미친다.  
- Class Method - Class로 호출  
  - @classmethod 데코레이터를 사용해서 클래스에 메서드를 선언하면 해당 메서드는 클래스(class) 메서드  
  - 첫번째 매개변수로 클래스 자체가 넘어 오며, 첫번째 매개변수명은 보통 cls라고 선언한다.   
  - 첫번째 매개변수 cls를 통해 클래스 속성에 접근하거나, 클래스 메서드를 호출 할 수 있다. 
  - Class 메서드의 경우, 클래스 레벨로 호출되기 때문에, 클래스 멤버 변수만 변경이 가능하다.   
- Static Method - Class로 호출  
  - @staticmethod 데코레이터를 사용해서 클래스에 메서드를 선언하면 해당 메서드는 정적(static) 메서드  
  - 인스턴스 메서드나 클래스 메서드와 달리 첫번째 매개변수가 할당되지 않는다.  
  - 정적 메서드 내에서는 인스턴스/클래스 속성에 접근이나 호출이 불가능하다.  

```python
class testClass:
    def __init__(self, name, nationality): # 생성자
        self.name = name
        self.nationality = nationality
    
    @classmethod #데코레이터(decorator)를 선언해줘야 함
    def initData(cls, value1, value2): #첫번째 인자로 클래스를 받음
        return cls(value1, value2)
        

tc1 = testClass.initData('python', 'korea')
print(tc1.name, tc1.nationality)

Output
python korean

class testStaticClass: # 유틸리티성 클래스를 만들 때 사용
    @staticmethod   #데코레이터(decorator)를 선언해줘야 함
    def add(value1, value2):
        return value1 + value2
    
    @staticmethod   #데코레이터(decorator)를 선언해줘야 함 
    def Minus(value1, value2): 
        return value1 - value2
        
tsc1 = testStaticClass.add(10, 20) #객체 생성 없이 바로 클래스로 호출
tsc2 = testStaticClass.Minus(100, 20) #객체 생성 없이 바로 클래스로 호출

print(tsc1, tsc2)

Output
30, 80
```

## Object  
- Class로 생성되어 구체화 된 객체(인스턴스)  
- Python에서 사용하는 string, int, list, dict 등 모든게 다 객체(인스턴스)  
- 실제로 Class가 인스턴스화 되어 메모리에 상주하는 상태를 의미  
- Class가 빵틀이라면, Object는 빵틀로 찍어낸 빵이라고 비유 할 수 있음  

