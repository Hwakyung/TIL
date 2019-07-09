# StartCamp day_02

### 심화학습

- 마우스의 개념이 들어와서 조작의 개념이 바꿔짐 - > 상용화의 계기

- CLI (command line interface) : 텍스트 터미널을 통해서 사용자와 컴퓨터가 상호작용하는 방식
  

###  bash  명령어 기초 

    1. ls : 현재 디렉토리 파일들을 나열
    2. cd (change directory) : 현재 작업하는 디렉토리를 변경
    3. mkdir(make directory) : 새로운 디렉토리 생성
    4. echo : 문자열 출력
    5. rm : 파일 지우기
    6. pwd (present working directory) : 현재 어디 위치에 있는지 확인
    7. touch : 파일 만드기
    8. exit : 종료
    9. mv : 파일 옮기기




#### (예시)웹 브라우저 조작하기


``` python
import webbrowser

webbrowser.open('naver.com')
```

> webrrowser라는 묘듈을 import를 통해서 불러올 수 있다.
>
> webbrowser.open(url) => 웹 브라우저를 열기 위한 메소드

``` python
import webbrowser

url = "https://search.naver.com/search.naver?sm=top_hty&fbm=0&ie=utf8&query="
my_keywords = ['iu','bts','winner','blockb']
for i in my_keywords :
    webbrowser.open(url + i)

```

> 검색창 url 정보를 가져와 원하는 검색어 정보를 리스트에 저장하고 이를 for 구문을 통해서 웹브라우저의 url 정보와 검색어 정보를 합쳐 검색 결과 창을 나타나게 한다.



### 웹 크롤링하기 

- 크롤링 : 웹에서 원하는 데이터를 가져오는 것

- requests : 파이썬에서 HTTP 요청을 보내는 모듈

- BeautifulSoup :  HTML document를 파싱해주는 것

   - select(selector) : 문서 안에 있는 특정 내용을 뽑아주는 것

   - select_one(selector) : 문서 안에 하나의 내용을 뽑아주는 것

- 코스피 지수 확인하기 
 ```python
import requests 
from bs4 import BeautifulSoup
  
response = requests.get('https://finance.naver.com/sise/').text
soup = BeautifulSoup(response, 'html.parser')
kospi = soup.select('#KOSPI_now')
print(kospi)
 ```
> BeautifulSoup 라이브러리를 사용하기 위해서는 먼저 bs4를  import를 해야 한다.
>
> requests를 통해 원하는 데이터를 얻고 text로 변환한다.
>
> BeautifulSoup을 통해 데이터를 파싱해주고 그 중  #KOSPI_now (''#''은 아이디를 나타내는 것)를 선택 
>
> kospi를 출력한다.

- 네이버 실시간 검색어 1위를 가져오기 

``` python
import requests
from bs4 import BeautifulSoup

response = requests.get('https://www.naver.com/').text
soup = BeautifulSoup(response, 'html.parser')
naver = soup.select_one('#PM_ID_ct > div.ㅊㅇ se > ul:nth-child(5) > li:nth-child(1) > a.ah_a > span.ah_k')
print(naver.text)

```

- faker 파일 정보 만들기 

``` python
from faker import Faker
import os # 운영체제에 맞는 시스템을 돌려주는 것
f = Faker('ko_KR')

for i in range(100) :
    filename = f'{i}_{f.name()}.txt'
    cmd = f'touch {filename}'
    os.system(cmd) #시스템 명령어를 호출하여 파일 생성
```

> faker라는 묘듈을 import 하여  반복문을 통해서 100개의 랜덤한 이름을 가진 파일을 생성

- 'SAMSUNG_'이라는 말머리를 가진 파일 이름을  'SSAFY__'이란 말머리로 바꾸기
``` python 
import os 

os.chdir(r"C:\Users\student\startcamp\students") # raw : 백슬래쉬의 용도를 얻기 위해서
for filename in os.listdir('.'):
    os.rename(filename, filename.replace("SAMSUNG_", "SSAFY_")) 
```
> 


### Git 

- (분산) 버전 관리 시스템 프로젝트의 수정 및 변경 사항 비교 분석 및 병합도 가능

- 협업을 하기 위해서 github를 사용해야 함

  
### Github 사용하기 
1. git init : 사용할 폴더를 git으로 관리하겠다고 입력함.
2. git add . : 원하는 파일을 추가
3. git commit -m "" : 로컬 저장소에 변경사항을 커밋
4. git push origin master : 원하는 파일을 원격 저장소에 저장

- 원하는 파일 가져오기
  - git clone : 저장소 복제하기
  - git push origin master :  변경할 파일을 원경 저장소에 보내기
  - git pull origin master : 전체 파일을 가져오는 것이 아닌 변경된 파일만 가져오는 것

