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

```python

class testClass:
    def __init__(self): # 생성자
        self.name = 'test'
        self.nationality = 'python'
        
t1 = testClass() # Class 생성 시 생성자가 호출
print(t1.name, t1.nationality)


class testClass:
    def __init__(self, name, nationality): # 생성자
        self.name = name
        self.nationality = nationality
        
t1 = testClass('user', 'korea') # Class 생성 시 초기값 설정
print(t1.name, t1.nationality)


class testClass:
    def __init__(self, name, nationality): # 생성자
        self.name = name
        self.nationality = nationality
        
    def printData(self): # Method printData 이므로 가장 맨 앞은 self 가 온다.
        print(self.name, self.nationality)
        
t1 = testClass('user', 'korea') # Class 생성 시 초기값 설정
t1.printData()

```

## Object  
- Class로 생성되어 구체화 된 객체(인스턴스)  
- Python에서 사용하는 string, int, list, dict 등 모든게 다 객체(인스턴스)  
- 실제로 Class가 인스턴스화 되어 메모리에 상주하는 상태를 의미  
- Class가 빵틀이라면, Object는 빵틀로 찍어낸 빵이라고 비유 할 수 있음  



