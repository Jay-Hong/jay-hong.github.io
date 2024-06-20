---
title:  🌵 Python Basic 🌱
categories: Python
tag: [🌵 python, 🌱 basics]
toc: true
excerpt: false
---

이번 포스팅에서는 Python의 기본적인 사용법을 알아보자. <br> Python 기본 입출력, '**문자열**' 다루기(연습), [ `List` , `Tuple` , `Dict` , `Set` ] 등이 포함 된다.

💡 🔩 ⚙️ 🍀 🍌 👉 ⚡️ 💥 🔥 🌈 ✏️

## 기본 입출력


```python
name = input()
```

    Jay


```python
name = input('Waht is your name?')
```

    Waht is your name?Jay Hong


```python
name
```

    'Jay Hong'



```python
digit_str = '123'
digit_int = int(digit_str)
print (type(digit_int))
```

    <class 'int'>



```python
int(input('How old are you?'))
```

    How old are you?34

    34


```python
print (2 ** 4)  # 2의4승
```

    16

<br>
## 문자열 다루기


```python
article = """A man who opened the emergency door of an Asiana Airlines plane just before landing on Friday afternoon told police that he felt suffocated and wanted to get off the plane quickly.

The door of the jet opened as it was coming in to land in Daegu, South Korea, leaving wind whipping through the plane’s cabin as terrified passengers gripped their armrests, video of the incident shows.

An airline official said a man in his 30s who was sitting at the emergency seat seemed to have opened the door when the aircraft was about 700 feet (213 meters) above the ground and about two to three minutes from landing in the city 150 miles (240 kilometers) south of Seoul.

However, company officials told CNN the plane had landed safely.

According to the Daegu Fire Department, 12 people suffered minor injuries from hyperventilation and nine of them have been sent to hospitals in Daegu.

The aircraft was identified on the Flightradar 24 tracking website as an Airbus 321.

Thomas noted that the landing speed of an A321 is about 150 knots (172 mph), meaning winds of that speed are passing the aircraft. The door, behind the wing of the aircraft, opened into that airstream, he said.

“It seems implausible that the door could be opened in the first place and then against the airstream technically impossible, but somehow or another it has happened,” Thomas said.

Asiana Airlines told CNN: “The airplane is automatically set to adjust the pressure of the cabin according to the altitude of the aircraft. When the aircraft is high up in the air, it is impossible to open the door but when the altitude is low and close to landing, the door can be opened.”"""
```


```python
article.count('\n')
```




    16




```python
len(article)
```




    1651




```python
article.find('C')
```




    696




```python
article.replace("A man", "JP")
```

    'JP who opened the emergency door of an Asiana Airlines plane just before landing on Friday afternoon told police that he felt suffocated and wanted to get off the plane quickly.\n\nThe door of the jet opened as it was coming in to land in Daegu, South Korea, leaving wind whipping through the plane’s cabin as terrified passengers gripped their armrests, video of the incident shows.\n\nAn airline official said a man in his 30s who was sitting at the emergency seat seemed to have opened the door when the aircraft was about 700 feet (213 meters) above the ground and about two to three minutes from landing in the city 150 miles (240 kilometers) south of Seoul.\n\nHowever, company officials told CNN the plane had landed safely.\n\nAccording to the Daegu Fire Department, 12 people suffered minor injuries from hyperventilation and nine of them have been sent to hospitals in Daegu.\n\nThe aircraft was identified on the Flightradar 24 tracking website as an Airbus 321.\n\nThomas noted that the landing speed of an A321 is about 150 knots (172 mph), meaning winds of that speed are passing the aircraft. The door, behind the wing of the aircraft, opened into that airstream, he said.\n\n“It seems implausible that the door could be opened in the first place and then against the airstream technically impossible, but somehow or another it has happened,” Thomas said.\n\nAsiana Airlines told CNN: “The airplane is automatically set to adjust the pressure of the cabin according to the altitude of the aircraft. When the aircraft is high up in the air, it is impossible to open the door but when the altitude is low and close to landing, the door can be opened.”'



<br>
```python
some_string = ",,,, computer ..."
print(some_string)
some_string.strip(',').strip('.').strip()
```

    ,,,, computer ...

    'computer'



<br>
```python
print("I have a {}, I have an {}.".format("pen", "apple"))
```

    I have a pen, I have an apple.


<br>
```python
interest = 0.887
print(format(interest, ".2f"))
```

    0.89


<br>
```python
data = 100
str(100)

```

    '100'



<br>
```python
data = input('주민번호를 입력하세요')
data[0:2]
```

    주민번호를 입력하세요820317

    '82'



<br>
```python
# 1~10 총 합 출력
sum = 0
for i in range(1, 11):
    sum = sum + i
    # print(i, sum)
print(sum)
```

    55


<br>
```python
num = int(input("2~9사이에 숫자를 입력하세요"))

for index in range(1,10):
    print(num, 'X', index, '=', num*index)
```

    2~9사이에 숫자를 입력하세요6
    6 X 1 = 6
    6 X 2 = 12
    6 X 3 = 18
    6 X 4 = 24
    6 X 5 = 30
    6 X 6 = 36
    6 X 7 = 42
    6 X 8 = 48
    6 X 9 = 54


<br>
```python
raw_data = "Jay,Andy,Justin,Arthor"

data = raw_data.split(',')

for str_data in data:
    print(str_data)
```

    Jay
    Andy
    Justin
    Arthor

<br>
### 문자열 출력 (참고)
* print("I have a %s, I have an %s." % ("pen","apple"))
  - %s - string
  - %c - character
  - %d - int
  - %f - float


```python
print("I have a %s, I have an %s." % ("pen","apple"))
```

    I have a pen, I have an apple.

<br>
<br>
## 문자열 다루기 연습


```python
string = 'Jay-Hong\'s ID is jayhong'
string.count('H')   # 문자열에 H 가 몇번 나올까요 (대소문자 구별함)
```




    1



<br>
```python
string = 'Jay-Hong\'s ID is jayhong'
string.index('i')
```




    14



<br>
```python
string = 'Jay-Hong\'s ID is jayhong'
string.index('x')    # str.index('찾을문자') 는 찾을문자 가 없으면 에러 난다ㅠㅠ
```


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    Cell In[4], line 2
          1 string = 'Jay-Hong\'s ID is jayhong'
    ----> 2 string.index('x')


    ValueError: substring not found


<br>
```python
string = 'Jay-Hong\'s ID is jayhong'
string.find('x')
# .find 찾는 문자 없으면 "-1", 있으면 몇번째 인지 반환
```




    -1



<br>
```python
string = '12345'
comma = ','
comma.join(string)   # 껴넣을 문자.join(문자열)
```




    '1,2,3,4,5'



<br>
```python
data = "    Jay      "
data.strip()    # 앞 뒤 공백 다 지움
```




    'Dave'




```python
data = "    Jay      "
data.lstrip()    # 앞 쪽 공백 만 지움
```




    'Dave      '




```python
data = "    Jay      "
data.rstrip()    # 뒤 쪽 공백 만 지움
```




    '    Dave'




```python
data = "    99999999999(J(8 9)ay)88888888888888      "
data.strip(" 98()")    # string(" ") => 앞 뒤 따옴표 안에있는 문자 지움
```




    'J(8 9)ay'



<br>
```python
string = "Jay"
print(string)
print(string.upper())
print(string.lower())
```

    Jay
    JAY
    jay


<br>
```python
string = "Jay goes to USA"
string.split()
```




    ['Jay', 'goes', 'to', 'USA']




```python
string = "Jay goes to USA"
string.split()[3]
```




    'USA'




```python
string.split(' ')   # 명시적으로 스페이스를 기준으로 분리하겠다고 넣어줘도 됨
```




    ['Jay', 'goes', 'to', 'USA']




```python
string = "Jay/goes/to/USA"
string.split('/')
```




    ['Jay', 'goes', 'to', 'USA']



```python
string = "10,11,22,33,44"
split_string = string.split(',')

for index, split_item in enumerate(split_string):
    split_string[index] = int(split_item)
print(split_string)
```

    [10, 11, 22, 33, 44]


<br>
```python
string = "Jay goes to USA"
string.replace("David", "Dave")
```




    'Dave goes to Korea'




```python
string = "10,11,22,33,44"
string.replace(',',' ')
```




    '10 11 22 33 44'


<br>
<br>
## List / Tuple / Dict / Set


```python
data_list = list() # []
data_tuple = tuple() # ()
data_dict = dict() # {}
data_set = set()
```

### List 중복 제거 ( list -> set -> list )


```python
data_list = ['apple', 'dell', 'samsung', 'lg', 'apple', 'dell', 'samsung', 'lg', 'apple', 'dell', 'samsung', 'lg']
print(data_list)
data = set(data_list)
print(data)
data_list = list(data)
print(data_list)
```

    ['apple', 'dell', 'samsung', 'lg', 'apple', 'dell', 'samsung', 'lg', 'apple', 'dell', 'samsung', 'lg']
    {'samsung', 'dell', 'apple', 'lg'}
    ['samsung', 'dell', 'apple', 'lg']


### Set


```python
# set 예제
ppaq = {'pen', 'apple', 'pineapple', 'pen'}
print(ppaq)

print('apple' in ppaq)
print('applepen' in ppaq)

pineapple = set('pineapple')
print(pineapple)
```

    {'pineapple', 'apple', 'pen'}
    True
    False
    {'p', 'i', 'n', 'e', 'a', 'l'}



```python
set_a = {1,2,3,4,5}
print(set_a)
set_a.add('a')
print(set_a)
set_a.update({7,8,9})
print(set_a)
set_a.update([0,'df','sdd2'])
print(set_a)
set_a.remove(2) # 제거할 요소가 없으면 KeyError
print(set_a)
set_a.discard(2) # 제거할 요소가 없어도 에러 없음
print(set_a)
set_b = {1,3,5,7,9}
set_a = set_a - set_b
#set_a = set_a.difference(set_b)   #  - 연산자와 동일
#set_a.difference_update(set_b) # -= 연산자와 동일
print(set_a)
```

    {1, 2, 3, 4, 5}
    {1, 2, 3, 4, 5, 'a'}
    {1, 2, 3, 4, 5, 7, 8, 9, 'a'}
    {0, 1, 2, 3, 4, 5, 'df', 7, 8, 9, 'a', 'sdd2'}
    {0, 1, 3, 4, 5, 'df', 7, 8, 9, 'a', 'sdd2'}
    {0, 1, 3, 4, 5, 'df', 7, 8, 9, 'a', 'sdd2'}
    {0, 'df', 4, 8, 'a', 'sdd2'}


### Dictionary


```python
exchange = {'달러':1112, '위안':171, '엔':1010}
prices = '100 엔'

for exchange_item in exchange.keys():
    if prices[4:] == exchange_item:
        print(int(prices[:4]) * exchange[exchange_item], '원')

```

    101000 원


### Tuple 덕분에 변수끼리 값을 편하게 바꿀 수 있습니다


```python
x = y
y = x (x)

temp = x
x = y
y = temp

(x,y) = (y,x)
```

### Tuple 덕분에 함수에서 하나 이상의 값을 반환할 수도 있습니다


```python
def quot_and_rem(x,y):
    quot = x //y
    rem = x % y
    return (quot, rem)
(quot, rem) = quot_and_rem(3,10)
```


```python
def quot_and_rem(x,y):
    quot = x //y
    rem = x % y
    return quot, rem
quot, rem = quot_and_rem(3,10)
```


```python
print(quot)
print(rem)
```

    0
    3

