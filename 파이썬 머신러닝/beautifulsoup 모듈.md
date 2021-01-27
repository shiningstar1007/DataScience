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

## 다음 뉴스 데이터 추출  
 - https://news.v.daum.net/v/20210125201340317  
 - 뉴스기사에서 제목, 작성자, 작성일, 댓글 개수 추출  
 - tag를 추출할때는 가장 그 tag를 쉽게 특정할 수 있는 속성을 사용  
  - id의 경우 원칙적으로 한 html 문서 내에서 유일  

```python
import requests
from bs4 import BeautifulSoup

url = 'https://news.v.daum.net/v/20210125201340317'
resp = requests.get(url)


soup = BeautifulSoup(resp.text)
title = soup.find('h3', class_='tit_view') #기사 제목 찾기
print(title.get_text())


name = soup.find('span', class_='info_view') # 기자 이름 찾기
print(name.get_text())
name = name.find('span', class_='txt_info') # 결과 내 기자 이름 다시 찾기
print(name.get_text())  


Content = soup.find('div', id='kakaoContent') # 본문 내용 찾기
Contents = ''
for p in Content.find_all('p'):
    Contents += p.get_text().strip()
    
print(Contents)
```

## CSS를 이용하여 tag 찾기  
 - select, select_one함수 사용   
 - css selector 사용법  
   - 태그명 찾기 tag   
   - 자손 태그 찾기 - 자손 관계 (tag tag)  
   - 자식 태그 찾기 - 다이렉트 자식 관계 (tag > tag)  
   - 아이디 찾기 #id  
   - 클래스 찾기 .class  
   - 속성값 찾기 [name='test']  
     - 속성값 prefix 찾기 [name ^='test']  
     - 속성값 suffix 찾기 [name $='test']  
     - 속성값 substring 찾기 [name *='test]  
   - n번째 자식 tag 찾기 :nth-child(n)  

```python
import requests
from bs4 import BeautifulSoup

url = 'https://news.v.daum.net/v/20210125201340317'
resp = requests.get(url)
soup = BeautifulSoup(resp.text)

print(soup.select('h3')) # 태그명 찾기 tag 
print(soup.select('#kakaoContent')) # 아이디 찾기 #id
print(soup.select('#kakaoContent p')) # 아이디 찾기 #id 하위 내 p tag 찾기 (자손 태그 찾기 - 자손 관계 (tag tag))
print(soup.select('#kakaoContent > p')) # 아이디 찾기 #id 하위 내 p tag 찾기 (자식 태그 찾기 - 다이렉트 자식 관계 (tag > tag))
print(soup.select('h3'))
print(soup.select('h3.tit_cp')) #클래스 찾기 .class
print(soup.select('h3[class=tit_view]')) #속성값 찾기 [name='test']
print(soup.select('h3[class^=t]')) #속성값 prefix 찾기 [name ^='test']
print(soup.select('h3[class$="_view"]'))  #속성값 suffix 찾기 [name $='test']
print(soup.select('h3[class*="_"]'))  #속성값 substring 찾기 [name *='test]
print(soup.select('span.txt_info:nth-child(1)')) #n번째 자식 tag 찾기 :nth-child(n)
```


