---
title:  🍜 BeautifulSoup Basic 🌱
categories: Crawling
tag: [🍜 BeautifulSoup, 🌱 basics]
toc: true
excerpt: false
---


## BeautifulSoup Basic


```python
import requests
from bs4 import BeautifulSoup
res = requests.get('http://v.media.daum.net/v/20170615203441266')
soup = BeautifulSoup(res.content, 'html.parser')
mydata = soup.find('title')
print(mydata.get_text())
```

    잔금대출에도 DTI 규제 적용 검토


data = soup.find('p', class_='cssstyle)
data = soup.find('p', 'cssstyle')
data = soup.find('p', attrs = {'align' : 'center'})
data = soup.find(id='body')


```python
from bs4 import BeautifulSoup
html = """
<html>
    <body>
        <h1 id'title>[1]크롤링이랑?</h1>
        <p class='cssstyle'>웹페이지에서 필요한 데이터를 추출하는 것</p>
        <p id='body' align='center'>파이썬을 중심으로 다양한 웹크롤링 기술 발달</p>
    <body>
</html>
"""
soup = BeautifulSoup(html, 'html.parser')
# 태그로 검색 방법
data = soup.find('p', attrs={'id':'body', 'align':'center'})
#print(data)
print(data.string)
#print(data.get_text())
```

    파이썬을 중심으로 다양한 웹크롤링 기술 발달



```python
data = soup.find_all('p')
for item in data:
    print(item.string)
```

    웹페이지에서 필요한 데이터를 추출하는 것
    파이썬을 중심으로 다양한 웹크롤링 기술 발달



```python
import requests
from bs4 import BeautifulSoup

res = requests.get('http://v.media.daum.net/v/20170615203441266')
soup = BeautifulSoup(res.content, 'html.parser')

mydata = soup.find('div', 'layer_body')

detail = mydata.get_text()
detail
```




    '\n금융당국이 급증하는 가계부채 증가세를 막기 위해 아파트 잔금대출에도 소득을 따져 대출한도를 정하는 총부채상환비율(DTI)을 적용하는 방안을 유력하게 검토하고 있다.\n지금은 집값을 기준으로 대출한도를 매기는 주택담보인정비율(LTV) 규제만 적용돼 소득이 없어도 집값의 70%를 빌려 잔금을 치르는 게 가능하다.\n앞으로 잔금대출에 DTI가 적용되면 소득이 없는 사람은 집값의 70% 대출 받는 게 어려워진다.\n'




```python
import requests
from bs4 import BeautifulSoup

res = requests.get('https://davelee-fun.github.io/blog/crawl_test')
soup = BeautifulSoup(res.content, 'html.parser')

titles = soup.find_all('li', 'course')
for title in titles:
    print(title.get_text())
```

    (왕초보) - 클래스 소개
    (왕초보) - 블로그 개발 필요한 준비물 준비하기
    (왕초보) - Github pages 설정해서 블로그 첫 페이지 만들어보기
    (왕초보) - 초간단 페이지 만들어보기
    (왕초보) - 이쁘게 테마 적용해보기
    (왕초보) - 마크다운 기초 이해하고, 실제 나만의 블로그 페이지 만들기
    (왕초보) - 다양한 마크다운 기법 익혀보며, 나만의 블로그 페이지 꾸며보기
    (초급) - 강사가 실제 사용하는 자동 프로그램 소개 [2]
    (초급) - 필요한 프로그램 설치 시연 [5]
    (초급) - 데이터를 엑셀 파일로 만들기 [9]
    (초급) -     엑셀 파일 이쁘게! 이쁘게! [8]
    (초급) -     나대신 주기적으로 파이썬 프로그램 실행하기 [7]
    (초급) - 파이썬으로 슬랙(slack) 메신저에 글쓰기 [40]
    (초급) - 웹사이트 변경사항 주기적으로 체크해서, 메신저로 알람주기 [12]
    (초급) - 네이버 API 사용해서, 블로그에 글쓰기 [42]
    (중급) - 자동으로 쿠팡파트너스 API 로 가져온 상품 정보, 네이버 블로그/트위터에 홍보하기 [412]



```python
import requests
from bs4 import BeautifulSoup

res = requests.get('https://davelee-fun.github.io/blog/crawl_test')
soup = BeautifulSoup(res.content, 'html.parser')

section = soup.find('ul', id="dev_course_list")
titles = section.find_all('li', 'course')

for title in titles:
    print(title.get_text())
```

    (초급) - 강사가 실제 사용하는 자동 프로그램 소개 [2]
    (초급) - 필요한 프로그램 설치 시연 [5]
    (초급) - 데이터를 엑셀 파일로 만들기 [9]
    (초급) -     엑셀 파일 이쁘게! 이쁘게! [8]
    (초급) -     나대신 주기적으로 파이썬 프로그램 실행하기 [7]
    (초급) - 파이썬으로 슬랙(slack) 메신저에 글쓰기 [40]
    (초급) - 웹사이트 변경사항 주기적으로 체크해서, 메신저로 알람주기 [12]
    (초급) - 네이버 API 사용해서, 블로그에 글쓰기 [42]
    (중급) - 자동으로 쿠팡파트너스 API 로 가져온 상품 정보, 네이버 블로그/트위터에 홍보하기 [412]



```python
import requests
from bs4 import BeautifulSoup

res = requests.get('https://davelee-fun.github.io/blog/crawl_test')
soup = BeautifulSoup(res.content, 'html.parser')

section = soup.find('ul', id="dev_course_list")
titles = section.find_all('li', 'course')

for title in titles:
    print(title.get_text().split('[')[0].split('-')[1].strip())
```

    강사가 실제 사용하는 자동 프로그램 소개
    필요한 프로그램 설치 시연
    데이터를 엑셀 파일로 만들기
    엑셀 파일 이쁘게! 이쁘게!
    나대신 주기적으로 파이썬 프로그램 실행하기
    파이썬으로 슬랙(slack) 메신저에 글쓰기
    웹사이트 변경사항 주기적으로 체크해서, 메신저로 알람주기
    네이버 API 사용해서, 블로그에 글쓰기
    자동으로 쿠팡파트너스 API 로 가져온 상품 정보, 네이버 블로그/트위터에 홍보하기



```python
import requests
from bs4 import BeautifulSoup

res = requests.get('https://davelee-fun.github.io/blog/crawl_test')
soup = BeautifulSoup(res.content, 'html.parser')

section = soup.find('ul', id="dev_course_list")
titles = section.find_all('li', 'course')

for index, title in enumerate(titles):
    print(str(index + 1) + '.', title.get_text().split('[')[0].split('-')[1].strip())
```

    1. 강사가 실제 사용하는 자동 프로그램 소개
    2. 필요한 프로그램 설치 시연
    3. 데이터를 엑셀 파일로 만들기
    4. 엑셀 파일 이쁘게! 이쁘게!
    5. 나대신 주기적으로 파이썬 프로그램 실행하기
    6. 파이썬으로 슬랙(slack) 메신저에 글쓰기
    7. 웹사이트 변경사항 주기적으로 체크해서, 메신저로 알람주기
    8. 네이버 API 사용해서, 블로그에 글쓰기
    9. 자동으로 쿠팡파트너스 API 로 가져온 상품 정보, 네이버 블로그/트위터에 홍보하기


## selector


```python
import requests
from bs4 import BeautifulSoup

res = requests.get('https://davelee-fun.github.io/blog/crawl_test')
soup = BeautifulSoup(res.content, 'html.parser')

items = soup.select('h3')
for item in items:
    print(item.get_text())
```

    나만의 엣지있는 블로그 사이트 만들기
    당신의 커리어에 파이썬을 입히세요! 자신만의 자동 프로그램까지 가져가는 특별한 강의



```python
import openpyxl

def write_excel_template(filename, sheetname, listdata):
    excel_file = openpyxl.Workbook()
    excel_sheet = excel_file.active
    excel_sheet.column_demensions['A'].width = 100
    
    if sheetname != '':
        excel_sheet.title = sheetname
        
    for item in listdata:
        excel_sheet.apend(item)
    excel_file.save(filename)
    excel_file.close()
```
