# Python 정규표현식  

## 정규표현식 (Regular Expression)  
- 특정한 패턴과 일치하는 문자열를 '검색', '치환', '제거' 하는 기능을 지원한다.  
- 정규표현식의 도움없이 패턴을 찾는 작업(Rule 기반)은 불완전 하거나, 작업의 cost가 높다.  
- 예를들어 이메일 형식 판별, 전화번호 형식 판별, 숫자로만 이루어진 문자열 등이 있다.  
- Crawling 에서도 많이 사용함  
- 정규표현식을 사용하기 위해서는 re 를 import 해서 사용한다.

## raw string   
- 문자열 앞에 r이 붙으면 해당 문자열이 구성된 그대로 문자열로 변환한다.  

```python
a = 'abc\n'
b = r'abc\n' # \n 도 문자열로 취급
print(a)
print(b)

Output
abc
abc\n
```

## 기본 패턴  
- a, Z, 9 등등.. 문자 하나하나의 character들은 정확히 해당 문자와 일치  
  - 예를들어 패턴 test는 test 문자열과 일치  
  - 대소문자의 경우 기본적으로 구별하나, 구별하지 않도록 설정 가능하다.  
- 몇몇 문자들에 대해서는 예외가 존재하는데, 이들은 특별한 의미로 사용 됨    
  - . ^ $ * + ? { } [ ] \ | ( )  
- . (마침표) : 어떤 한개의 character와 일치 (newline(엔터) 제외)  
- \w : 문자 character와 일치 [a-zA-Z0-9_]  
- \s : 공백문자와 일치  
- \t, \n, \r : tab, newline, return  
- \d : 숫자 character와 일치 [0-9]  
- ^ = 시작, $ = 끝 각각 문자열의 시작과 끝을 의미  
- \가 붙으면 스페셜한 의미가 없어짐. 예를들어 \\.는 .자체를 의미 \\\는 \를 의미  
- 참조 링크 : https://docs.python.org/3/library/re.html  

## Search Method  
- 첫번째로 패턴을 찾으면 Match 객체를 반환하고, 못찾으면 None을 반환한다.  

```python
import re
data = r'@#$%QWERtyuiab5fepythondf77td'

print(re.search(r'python1', data))
print(re.search(r'python', data))
print(re.search(r'\d\d', data))
print(re.search(r'\d\w', data))
print(re.search(r'..\w\w', data))

Output
None
<re.Match object; span=(17, 23), match='python'>
<re.Match object; span=(25, 27), match='77'>
<re.Match object; span=(14, 16), match='5f'>
<re.Match object; span=(2, 6), match='$%QW'>
``

## [](Square Brackets) 문자들의 범위를 나타내기 위해 사용  
- 대괄호는 or를 의미한다.
- [] 내부의 메타 캐릭터는 캐릭터 자체를 나타냄  
  - [abkx] : a or b or k or x   
  - [ab.^] : a or b or . or ^  
  - [a-h]  : -와 함께 사용되면 해당 문자 사이의 범위에 속하는 문자 중 하나  
  - [0-9]  : 모든 숫자  
  - [a-z]  : 모든 소문자  
  - [A-Z]  : 모든 대문자  
  - [a-zA-Z0-9] : 모든 알파벳 문자 및 숫자  
  - [^0-9] : ^가 맨 앞에 사용 되는 경우 해당 문자 패턴이 아닌 것과 매칭(^은 NOT를 의미)  

```python
data = r'pythonworld2021testmission'

print(re.search(r'[ach]on', data))
print(re.search(r'[0-5]test', data))
print(re.search(r'[abcd.^]2021', data))
print(re.search(r'[^abcd.]2021', data))

Output
<re.Match object; span=(3, 6), match='hon'>
<re.Match object; span=(14, 19), match='1test'>
<re.Match object; span=(10, 15), match='d2021'>
None
```

## \(backslash)   
- 다른 문자와 함께 사용되어 특수한 의미를 지님  
 - \d : 숫자를 [0-9]와 동일  
 - \D : 숫자가 아닌 문자  [^0-9]와 동일  
 - \s : 공백 문자(띄어쓰기, 탭, 엔터 등)  
 - \S : 공백이 아닌 문자  
 - \w : 알파벳대소문자, 숫자 [0-9a-zA-Z]와 동일  
 - \W : non alpha-numeric 문자 [^0-9a-zA-Z]와 동일  
- 메타 캐릭터가 캐릭터 자체를 표현하도록 할 경우 사용  
 - \. , \\  

```python
data = r'python world. 2021 Test mission class'

print(re.search(r'\smission', data))
print(re.search(r'\west', data))
print(re.search(r'\.', data))

Output
<re.Match object; span=(23, 31), match=' mission'>
<re.Match object; span=(19, 23), match='Test'>
<re.Match object; span=(12, 13), match='.'>
```

## .   
- 모든 문자를 의미  

```python
data = r'python world. 2021 test mission class'

print(re.search(r'wo.ld', data))

Output
<re.Match object; span=(7, 12), match='world'>
```

## 반복패턴  
- 패턴 뒤에 위치하는 *, +, ?는 해당 패턴이 반복적으로 존재하는지 검사   
 - '+' : 1번 이상의 패턴이 발생  
 - '*' : 0번 이상의 패턴이 발생  
 - '?' : 0 혹은 1번의 패턴이 발생  
- 반복 패턴의 경우 가능한 많은 부분이 매칭되도록 검색하여 반환함  

```python
data = r'qwerabcbdccbasdf'

print(re.search(r'a[bcd]*b', data))

Output
data = r'qeraabcbdccbaaasdftp:\\192.168.152.111'

print(re.search(r'a[bcd]*b', data))
print(re.search(r'a\w+c', data))
print(re.search(r'qw+e', data)) # 1번 이상 가장 처음 매칭 된 위치를 반환
print(re.search(r'qw*e', data)) # 0번 이상 가장 처음 매칭 된 위치를 반환
print(re.search(r'ftp?', data))

Output
<re.Match object; span=(4, 12), match='abcbdccb'>
<re.Match object; span=(3, 11), match='aabcbdcc'>
None
<re.Match object; span=(0, 2), match='qe'>
<re.Match object; span=(17, 20), match='ftp'>
```

## ^, $  
- ^  문자열의 맨 앞부터 일치하는 경우 검색  
- \$  문자열의 맨 뒤부터 일치하는 경우 검색  

```python
print(re.search(r'^a\w+c', 'cabcdefgh'))
print(re.search(r'a\w+c', 'cabcdefgh'))
print(re.search(r'e\w+g$', 'cabcdefgh'))
print(re.search(r'e\w+g', 'cabcdefgh'))

Output
None
<re.Match object; span=(1, 4), match='abc'>
None
<re.Match object; span=(5, 8), match='efg'>
```

## Grouping  
- ()을 사용하여 그루핑  
- 매칭 결과를 각 그룹별로 분리 가능  
- 패턴 명시 할 때, 각 그룹을 괄호() 안에 넣어 분리하여 사용  

```python
ret = re.search(r'(\w+)@(.+)', 'testuser@python.com')

print(ret)
print(ret.group())
print(ret.group(1))
print(ret.group(2))

Output
<re.Match object; span=(0, 19), match='testuser@python.com'>
testuser@python.com
testuser
python.com
```

## {}(curly brackets)  
- *, +, ?을 사용하여 반복적인 패턴을 찾는 것이 가능하나, 반복의 횟수 제한은 불가  
- 패턴뒤에 위치하는 중괄호{}에 숫자를 명시하면 해당 숫자 만큼의 반복인 경우에만 매칭  
- {4} - 4번 반복  
- {3,4} - 3 ~ 4번 반복  

```python
data = r'qeraabcbdccbaaabdftp:'

print(re.search(r'ba{2}b', data))
print(re.search(r'ba{3}b', data))
print(re.search(r'ba{2,5}b', data))

Output
None
<re.Match object; span=(11, 16), match='baaab'>
<re.Match object; span=(11, 16), match='baaab'>
```

## 미니멈 매칭(non-greedy way)  
- 기본적으로 *, +, ?를 사용하면 Maximum 매칭으로 동작한다.  
- *?, +?을 이용하여 해당 기능을 구현  

```python
ret = re.search(r'<.+?>', '<html>testuser@python.com</html>')

print(ret)

Output
<re.Match object; span=(0, 6), match='<html>'>
```

## {}?  
- {m,n}의 경우 m번 에서 n번 반복하나 greedy하게 동작  
- {m,n}?로 사용하면 non-greedy하게 동작. 즉, 최소 m번만 매칭하면 만족  

```python
data = r'qerbaabcbdccbaaabdftp:'

print(re.search(r'ba{2,5}?b', data))

Output
<re.Match object; span=(3, 7), match='baab'>
```

## match  
- search와 유사하나, 주어진 문자열의 시작부터 비교하여 패턴이 있는지 확인  
- 시작부터 해당 패턴이 존재하지 않다면 None 반환  

## findall  
- search가 최초로 매칭되는 패턴만 반환한다면, findall은 매칭되는 전체의 패턴을 반환  
- 매칭되는 모든 결과를 리스트 형태로 반환  

## sub  
- 주어진 문자열에서 일치하는 모든 패턴을 replace  
- 그 결과를 문자열로 다시 반환함  
- 두번째 인자는 특정 문자열이 될 수도 있고, 함수가 될 수 도 있음  
- count가 0인 경우는 전체를, 1이상이면 해당 숫자만큼 치환 됨  

## compile  
- 동일한 정규표현식을 매번 다시 쓰기 번거로움을 해결  
- compile로 해당표현식을 re.RegexObject 객체로 저장하여 사용가능  

```python
email_reg = re.compile(r'[\w-]+@[\w.]+')
email_reg.search('my e-mail address is test@python.com')

Output
<re.Match object; span=(21, 36), match='test@python.com'>
```


