---
title:  🚧 환율정보 크롤링 (진행중)... 🚧
categories: Crawling
tag: [🌵 python, 🍜 BeautifulSoup, ✅ Selenium]
toc: true
excerpt: false
---

## 은행별 고시환율 크롤링
```python
import requests
from bs4 import BeautifulSoup

#inputURL = input()
#res = requests.get(inputURL)
mibank_exchange = 'https://www.mibank.me/exchange/bank/index.php?search_code='
banks = {'hana':'005', 'kukmin':'004','ibk':'003','woori':'020','shinhan':'088','nh':'011','busan':'032','citi':'027','SC':'023'}

for bank in banks:
    res = requests.get(mibank_exchange + banks[bank])
    soup = BeautifulSoup(res.content, 'html.parser')
    item = soup.select_one('body > div.container_sub_banks_saving > div.right_contents > div.box_contents1 > table > tbody > tr:nth-child(3) > td.right.counter.rollsty01')
    print(bank, '     \t', item.get_text())
```

    hana      	 1262.90
    kukmin      	 1262.60
    ibk      	 1262.80
    woori      	 1263.20
    shinhan      	 1262.60
    nh      	 1263.10
    busan      	 1262.75
    citi      	 1262.80
    SC      	 1262.95


## headless 옵션
```python
from selenium import webdriver; import time
from selenium.webdriver.common.keys import Keys
from selenium.webdriver.common.by import By
from selenium.webdriver.chrome.service import Service
from webdriver_manager.chrome import ChromeDriverManager

headlessoptions = webdriver.ChromeOptions()
headlessoptions.add_argument('headless')
headlessoptions.add_argument('window-size=1920x1080')
headlessoptions.add_argument("disable-gpu")
headlessoptions.add_argument("User-Agent:  Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/114.0.0.0 Safari/537.36")
headlessoptions.add_argument("lang=ko_KR")
driver = webdriver.Chrome(service=Service(ChromeDriverManager().install()), options=headlessoptions)

# driver = webdriver.Chrome(service=Service(ChromeDriverManager().install()))

# 크롤링할 사이트 호출
driver.get("https://kr.investing.com/currencies/usd-krw")

time.sleep(0)

# 여기에 작성해보세요
element = driver.find_element(By.CSS_SELECTOR, "#__next div.instrument-price_instrument-price__2w9MW.flex.items-end.flex-wrap.font-bold > span")
print(element.text)
#element.clear()
element = driver.find_element(By.CSS_SELECTOR, "#__next div.instrument-metadata_time__fopxP > time")
print(element.text)
driver.quit()

```

    1,264.92
    17:15:44


## investing.com 달러환율 크롤링

```python
from urllib.request import Request, urlopen
from bs4 import BeautifulSoup; import time

req = Request('https://kr.investing.com/currencies/usd-krw', headers={'User-Agent': 'Mozilla/5.0'})
html = urlopen(req)
soup = BeautifulSoup(html, 'html.parser')

time.sleep(0)

dollar = soup.find("span", attrs={"class":"text-2xl"}).get_text()
dollar = float(dollar.replace(",", ""))

print(dollar)
```

    1264.92

