---
title:  크롤링 중 IP 차단을 피하는 전략과 기법 🛡️
categories: Crawling
tag: [🌵 python, 🍜 BeautifulSoup, ✅ Selenium]
toc: true
excerpt: false
---
​
# 크롤링 중 IP 차단을 피하는 전략과 기법 🛡️
​
## 1. IP 차단의 이유와 원리 🚫

먼저, IP 차단은 왜 발생할까요? 대부분의 웹사이트는 과도한 트래픽으로 인한 서버 부하를 방지하거나, 불법 크롤링을 막기 위해 일정량 이상의 요청을 한 IP에서 감지하면 그 IP를 일정 시간 동안 접근 제한합니다. 또한, robots.txt 파일에서 크롤링을 금지한 페이지에 반복적으로 접근하면 차단될 수도 있습니다.

​

## 2. User-Agent 변경 🕶️

크롤링 시 사용하는 User-Agent를 자주 바꿔주는 것이 좋습니다. 일관된 User-Agent를 사용하면 크롤러로 인식될 가능성이 높아지기 때문입니다. 여러 User-Agent를 리스트로 만들어 랜덤하게 변경하면서 사용하세요.

```python
import random
import requests

USER_AGENTS = [
    'Mozilla/5.0 (Windows NT 10.0; Win64; x64) ...',
    'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_5) ...',
    ...
]

headers = {'User-Agent': random.choice(USER_AGENTS)}
response = requests.get('https://www.example.com', headers=headers)
```
​​
## 3. IP Rotation 🔄

가장 효과적인 방법 중 하나는 IP Rotation입니다. 여러 개의 프록시 IP를 활용하여 주기적으로 IP를 변경하는 것이죠. 이를 통해 웹 서버는 각각의 요청이 다른 사용자로부터 오는 것처럼 인식합니다.

```python
PROXIES = [
    {'http': 'http://10.10.1.10:3128', 'https': 'http://10.10.1.10:3128'},
    {'http': 'http://10.10.1.11:3128', 'https': 'http://10.10.1.11:3128'},
    ...
]

response = requests.get('https://www.example.com', proxies=random.choice(PROXIES))
```
​
## 4. 요청 간격 조절 ⏳

빠른 간격으로 반복적으로 요청을 보내면 크롤러로 인식될 확률이 높습니다. 따라서 time.sleep() 함수를 사용해 일정 시간 간격을 두고 요청을 보내는 것이 좋습니다.
```python
import time

for url in urls:
    response = requests.get(url)
    time.sleep(random.randint(2, 5))
```
​
## 5. 참조 페이지 사용 (Referer Header) 📄

크롤링 중 참조 페이지를 사용하면, 웹 서버는 해당 요청이 사용자의 정상적인 행동을 통해 이루어진 것으로 판단하기 쉽습니다. Referer Header를 사용하여 이전에 방문한 페이지 URL을 전송하세요.

```python
headers = {
    'User-Agent': random.choice(USER_AGENTS),
    'Referer': 'https://www.example.com/previous_page'
}
response = requests.get('https://www.example.com/target_page', headers=headers)
```
​
## 6. 쿠키 사용 🍪

로그인이 필요한 페이지나 세션 정보가 필요한 페이지는 쿠키를 사용하여 크롤링할 수 있습니다. requests의 Session 객체를 사용하면 쿠키를 유지하며 여러 요청을 보낼 수 있습니다.

```python
session = requests.Session()
response = session.get('https://www.example.com/login')
```

이 외에도 VPN 사용, headless browser의 사용 등 다양한 방법이 있습니다. 그러나, 항상 웹사이트의 서비스 이용 약관과 로봇 배제 표준(robots.txt)를 확인하고 크롤링하세요. 적절하지 않은 크롤링은 법적 문제를 초래할 수 있습니다.

​
## 7. 실제 적용 중 배운 것

1. webdriver.ChromeOptions() 에서 add_argument 할 때는 `''` (빈값=NULL) 이 들어가면 Error
2. 클래스 변수 호출 시에는 `인스턴스.클래스변수` , `self.클래스변수` 를 사용하는 것은 피한다 `Class명.클래스변수` 이렇게 사용하자

```python
import random

class ExampleSpider(scrapy.Spider):

    WINDOW_SIZES = [
        'window-size=1920x1080',
        'window-size=430x932',
        'window-size=428x926',
        '', # Error
        '', # Error
        'disable-gpu'
    ]

    def __init__(self):
        headlessoptions = webdriver.ChromeOptions()
        headlessoptions.add_argument('headless')
        # 혼돈을 피하기 위해 클래스 변수를 엑세스할 때는 클래스명을 사용하는 것이 좋다. 
        headlessoptions.add_argument(random.choice(ExampleSpider.LANG))
        headlessoptions.add_argument(random.choice(ExampleSpider.WINDOW_SIZES)) # NULL Error 가능성
        headlessoptions.add_argument(f"User-Agent: {random.choice(ExampleSpider.USER_AGENTS)}")
        self.driver = webdriver.Chrome(service=Service(ChromeDriverManager().install()), options=headlessoptions)
```

​

퀀트쇼의 개발 블로그 : <https://blog.naver.com/quantshow/223189297050>