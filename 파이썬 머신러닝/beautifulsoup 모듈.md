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

## 정규표현식으로 tag 찾기  

```python
import re
import requests
from bs4 import BeautifulSoup

url = 'https://news.v.daum.net/v/20210125201340317'
resp = requests.get(url)
soup = BeautifulSoup(resp.text)

print(soup.find_all(re.compile('h\d')))
print(soup.find_all('img', attrs = {'src' : re.compile('.+\.jpg')}))
print(soup.find_all('h3', class_=re.compile('.+view$')))
```

## 댓글 개수 추출하기  
 - 댓글의 경우, 최초 로딩시에 전달되지 않음  
 - 이 경우는 추가적으로 AJAX로 비동기적 호출을 하여 따로 data 전송을 함  
   - 개발자 도구의 network 탭에서 확인(XHR: XmlHTTPRequest)  
   - 비동기적 호출: 사이트의 전체가 아닌 일부분만 업데이트 가능하도록 함  
   - 4xx 오류 시 Request Headers 를 dict로 만들어서 파라미터로 넘겨서 사용한다.  

### HTTP 상태 코드  
 - 1xx (정보): 요청을 받았으며 프로세스를 계속한다  
 - 2xx (성공): 요청을 성공적으로 받았으며 인식했고 수용하였다  
 - 3xx (리다이렉션): 요청 완료를 위해 추가 작업 조치가 필요하다  
 - 4xx (클라이언트 오류): 요청의 문법이 잘못되었거나 요청을 처리할 수 없다  
 - 5xx (서버 오류): 서버가 명백히 유효한 요청에 대해 충족을 실패했다  
[출처: 위키피디아](https://ko.wikipedia.org/wiki/HTTP_%EC%83%81%ED%83%9C_%EC%BD%94%EB%93%9C)  

```python
import requests

url = 'https://comment.daum.net/apis/v1/ui/single/main/@20210125201340317'

headers = {
	'Authorization': 'Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJmb3J1bV9rZXkiOiJuZXdzIiwiZ3JhbnRfdHlwZSI6ImFsZXhfY3JlZGVudGlhbHMiLCJzY29wZSI6W10sImV4cCI6MTYxMTg3NjQyOSwiYXV0aG9yaXRpZXMiOlsiUk9MRV9DTElFTlQiXSwianRpIjoiNzUzMDhhN2QtODc2ZS00MDRmLWIzMjAtNmE3YmQ2MmYxYjBlIiwiZm9ydW1faWQiOi05OSwiY2xpZW50X2lkIjoiMjZCWEF2S255NVdGNVowOWxyNWs3N1k4In0.obOaZ3Uz1xfLfTRR1zYxIwdKBSxmwQuq51F9WzaWUGk',
	'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/88.0.4324.104 Safari/537.36',
	'Origin': 'https://news.v.daum.net',
	'Referer': 'https://news.v.daum.net/v/20210125201340317'
}

resp = requests.get(url, headers=headers)
resp.json()['post']['commentCount'] #댓글 개수 추출
```

## 로그인 후 데이터 크롤링  

- 실제 O마켓에 로그인해서 현재 내 포인트를 가져오기   

```python
import requests
from bs4 import BeautifulSoup

# 로그인 endpoint
url = 'https://signinssl.gmarket.co.kr/LogIn/LogInProc'

# id, password로 구성된 form data 생성하기
data = {'id' : 'kys3631', 'pwd' : '********'}

# 로그인 시도
s = requests.Session()

resp = s.post(url, data=data)
print(resp)

headers = {
    'Referer': 'myg.gmarket.co.kr',
    'Host': 'myg.gmarket.co.kr',
    'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/88.0.4324.104 Safari/537.36',
    'Cookie': 'pguid=***; sguid=***; jaehuid=***; charset=enUS; shipnation=KR; cguid=***; pcidx=***; PCIDJCN=***; isSFC=N; PCUID=***; WMONID=***; __RequestVerificationToken=***; user%5Finfo=safe%5Flogin=4&isMember=MEM&isDonatee=N&isZeroMargin=N&isEmailValid=Y&custType=PP&jaehuCustNo=TIxNR38jNzE2MczzNzY3OTU2Njh%2FRw%3D%3D&ageGroup=C&CR%5FType=I&corpIdNo=&clusterID=S000%3D0&toastYN=Y&pif=***&sif=***&ick=%***%3D&sbgid=***&time=2021%2D01%2D28+21%3A51%3A04&InterestGoodsCnt=0&InterestShopCnt=0&BuyShopCnt=8&jaehuPlatform=&adultAuth=***; ssguid=***'
}

my_page = 'http://myg.gmarket.co.kr/'
resp = s.get(my_page, headers=headers)

soup = BeautifulSoup(resp.text)

smilepoint = soup.find('li', class_='smilepoint')
point = smilepoint.find_all('span')
point[1].get_text()

Output
849
```