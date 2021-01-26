## beautifulsoup 모듈

- 문자열로 정의된 html 데이터 파싱
```python
from bs4 import BeautifulSoup

html = '''
<html>
  <head>
    <title>BeautifulSoup test</title>
  </head>
  <body>
    <div id='upper' class='test' custom='good'>
      <h3 title='Good Content Title'>Contents Title</h3>
      <p>Test contents</p>
    </div>
    <div id='lower' class='test' custom='nice'>
      <p>BeautifulSoup Test Python 1</p>
      <p>BeautifulSoup Test Python 2</p>
      <p>BeautifulSoup Test Python 3</p>
    </div>
  </body>
</html>'''

soup = BeautifulSoup(html)
```

### find 함수
- 특정 html tag를 검색
- 검색 조건을 명시하여 찾고자하는 tag를 검색

```python
print(soup.find('div')) #처음 검색되는 걸 찾는다.
print(soup.find('div', id='upper')) #키워드를 주고 검색 할 수 있다.
print(soup.find('div', class_='test')) #키워드가 class는 예약어이기 때문에 뒤에 _를 붙인다.

attrs = {'id' : 'upper', 'class':'test'} 
print(soup.find('div', attrs=attrs)) #키워드를 여러개 주고 싶을 때
```

### find_all 함수
- find가 조건에 만족하는 하나의 tag만 검색한다면, find_all은 조건에 맞는 모든 tag를 리스트로 반환

```python
print(soup.find_all('div'))
print(soup.find_all('div', id='upper')) #키워드를 주고 검색 할 수 있다.
```

## get_text 함수
- tag안에 value를 추출한다.
- 자식 tag를 가지고 있는 부모 tag 를 get_text()로 호출하면 자식 tag의 모든 value을 가져옴

```python
tag = soup.find('h3')
print(tag.get_text())

Output
'Contents Title'


tag = soup.find('div')
tag.get_text().strip()

Output
'Contents Title\n      Test contents'
```

## attribute 값 추출하기
- 경우에 따라 추출하고자 하는 값이 attribute에도 존재한다.
- 이 경우에는 검색한 tag에 attribute 이름을 [ ]연산을 통해 추출 가능하다.
- 예) div.find('h3')['title']

```python
tag = soup.find('h3')['title']
print(tag)

Output
Good Content Title
```