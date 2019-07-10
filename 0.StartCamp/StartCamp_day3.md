# StartCamp day3

- vscode에서 파일 생성하기
- 구버전

``` python
f = open("student.txt", "w") #파일을 여는데 w(write)라는 옵션
f.write('안녕하세요') #파일에 텍스트를 집어넣는 것
f.close() 
```
- open함수 내의 옵션
  - w : write (쓰기)
  - a : append (추가)
  - r : read (읽기)
- 새로운 버젼

``` python
import requests 
from bs4 import BeautifulSoup

url = 'https://finance.naver.com/marketindex/exchangeList.nhn'
response = requests.get(url).text
soup = BeautifulSoup(response, 'html.parser')
tr = soup.select('tbody > tr')

with open("kospi.txt", 'w') as f: # open이라는 함수를 통해서 열어주는 것을 with안에서는 f로 명칭
    for i in tr :
        f.write("{0}".format(i.select_one('.tit').text).strip() + ' : ')
        f.write("{0}".format(i.select_one('.sale').text) + '\n')
```

- csv: Comma-separated values의 약자로서 CSV 파일은 각 라인의 컬럼들이 콤마로 분리된 텍스트 파일 포맷
- with open('파일', 'w', encoding = 'utf-8', newline = '') as f => with 안에서는 파일을 f로 명칭, 한글을 인식하기 위해서 encoding을 'utf-8'로 한다.
- 웹 크롤링하여 csv 텍스트 파일 만들기

``` python
import csv
import requests
from bs4 import BeautifulSoup
url = 'https://finance.naver.com/marketindex/exchangeList.nhn'
response = requests.get(url).text
soup = BeautifulSoup(response, 'html.parser')

tr = soup.select('tbody > tr')
with open('naver_exchange.csv', 'w', encoding = 'utf-8', newline = '') as f :
    csv_writer = csv.writer(f)

    for r in tr :
        print(r.select_one('.tit').text.strip()) #공백을 제거해주는 메소드
        print(r.select_one('.sale').text)
        row = [r.select_one('.tit').text.strip(), r.select_one('.sale').text]
        csv_writer.writerow(row)

```

> 웹 사이트를 크롤링하여 데이터를 얻은 후, csv 모듈을 실행하기 위해 open()이라는 함수를 사용한다. 
>
> 파일과 모드를 선택한 수, csv_writer란 변수를 선정하여 csv.writer가 작성하는 정보를 할당한다.
>
> 리스트를 얻기위해서 for문을 사용하고 row라는 변수를 만들어, tit 클래스의 텍스트와,  sale 클래스의 텍스트를 안에 저장한다.
>
> csv_writer.writerow(row)를 이용하여 데이터를 리스트를 한 줄에 추가한다. 
> 

### HTML(HyperText Markup Language)

- HTML 이란? : 웹페이지를 뼈대를 이루는 마크업 언어
  - 마크업 : 구조를 이루어지는 것
-   HTML의 기본 구조
``` html
<!DOCTYPE html>
<html>   
    <head> 
    	
    </head>
    <body>
        '페이지의 내용들을 주로 입력'
    </body>
</html>
```
  - HTML 여러 태그들 

    1.  '<h1>' : 제목에 활용되는 태그

    2.  '<a>' : 다른 것과 연결하는데 사용되는 태그

    3. '<ol>' : ordered list 의 약자로 순서있는 리스트 태그
    
    4. '<input>' : 입력창 
    
    5. '<link>' : 외부 문서와 연결해주는 태그

- HTML은 단순한 구조를 만들어주기 때문에 이를 보기 좋게 수정하기 위해서는  CSS가 필요하며 더불어 동적인 업무를 수행하기 위해서는 자바스크립트 등이 사용된다. 
### CSS 
- CSS : 마크업 언어가 실제로 표시되는 방법을 기술하는 언어

- css에 적용하는 방법

  1. 태그 안에 작성 - 모든 태그에 적용가능
  2. 태그 밖에 <head></head>에 작성 

- HTML에 id를 지정하며 지정된 태그는 유니크한 이름을 지니게 된다. id는 고유한 이름으로 중복되어서는 안된다.  

  >``` <h1 id ='hello'></h1> : css에서는 #hello로 id를 지정할 수 있음
  ><h1 id ='hello'></h1> : css에서는 #hello로 id를 지정할 수 있음
  >```

- class는 같은 종류로 묶어주어 스타일을 지정할 수 있게 한다. ex)인스타의 태그

  > ```<h1 class = 'hi'></h1> : css에서는 .hi로 class를 지정할 수 있음
  > <h1 class = 'hi'></h1> : css에서는 .hi로 class를 지정할 수 있음
  > ```

- css의 적용에 클래스나 태그, 아이디가 충돌될 경우, 우선순위가 가장 높은 것을 최종적으로 선택하여 적용됨