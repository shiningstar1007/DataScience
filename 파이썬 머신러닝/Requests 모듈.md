# Requests 모듈  

- http request/response를 위한 모듈  
- HTTP Method를 메소드 명으로 사용하여 Request 요청  

## Get 요청하기  

```python
import requests

url = 'https://news.v.daum.net/v/20210125201340317'
resp = requests.get(url)
resp.text
```

## Post 요청하기  

```python
url = 'https://logins.daum.net/accounts/login.do?slevel=1'
data = { 'id' : 'zzz-_-darknight', 'pw' : '******'}
resp = requests.post(url, data=data)
```

## HTTP Header 데이터 이용하기  
- url 만으로 crawling이 안될 경우에 Request Headers 를 활용  
- Chrome 에서 개발자 도구를 들어가서 네트워크에 가보면 Headers 를 보면 Request Headers 에서 user-agent 를 활용  
- headres를 딕셔너리 형태로 생성하여 전달  

```python
import requests

url = 'https://news.v.daum.net/v/20210125201340317'
headers = {'user-agent' : 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/88.0.4324.104 Safari/537.36'}
resp = requests.get(url, headers=headers)
resp.text
```

