# selenium - 모듈  
 - 웹페이지 테스트 자동화용 모듈  
 - 개발/테스트용 드라이버(웹브라우저)를 사용하여 실제 사용자가 사용하는 것처럼 동작  
 - selenium 모듈 설치  (pip install selenium)  
   - [크롬 드라이버 다운로드](https://chromedriver.chromium.org/downloads)  

```python
from selenium import webdriver
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC
from selenium.webdriver.common.by import By
from bs4 import BeautifulSoup
import time

chrome_driver = '.\chromedriver.exe'
driver = webdriver.Chrome(chrome_driver)
url = 'https://www.python.org/'

driver.get(url)

search = driver.find_element_by_id('id-search-field') # 검색창 id

search.clear()
time.sleep(2)
search.send_keys('lambda') # 검색창에 lambda 입력
time.sleep(2)
search.send_keys(Keys.RETURN) #엔터
time.sleep(2)

driver.close()
```

```python
#다음 뉴스 웹사이트 크롤링 - 댓글 개수 획득하기

chrome_driver = '.\chromedriver.exe'
driver = webdriver.Chrome(chrome_driver)
url = 'https://news.v.daum.net/v/20210129181138371'
driver.get(url)

src = driver.page_source
soup = BeautifulSoup(src)

driver.close()

comment = soup.select_one('span.alex-count-area')
comment.get_text()
```

## selenium을 활용하여 특정 element의 로딩 대기  
 - WebDriverWait 객체를 이용하여 해당 element가 로딩 되는 것을 대기  
 - 실제로 해당 기능을 활용하여 거의 모든 사이트의 크롤링이 가능  
 - WebDriverWait(driver, 시간(초)).until(EC.presence_of_element_located((By.CSS_SELECTOR, 'CSS_RULE')))   

```python
# 네이버 뉴스 웹사이트 크롤링
chrome_driver = '.\chromedriver.exe'
driver = webdriver.Chrome(chrome_driver)
url = 'https://news.naver.com/main/read.nhn?mode=LSD&mid=shm&sid1=105&oid=028&aid=0002530759'
driver.get(url)

# 10초 동안 element를 기다려라, 무엇을? span.u_cbox_count 이 로딩될 때까지
WebDriverWait(driver, 10).until(EC.presence_of_element_located((By.CSS_SELECTOR, 'span.u_cbox_count'))) 

src = driver.page_source
soup = BeautifulSoup(src)

driver.close()

comment = soup.select_one('span.u_cbox_count')
comment.get_text()
```
 
