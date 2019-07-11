# StartCamp day04

### Flask​

- Flask란?
  - 파이썬 웹 어플리케이션을 만드는 Framwork

- Flask를 이용하여Hello world!라는 문자열 보여주기
``` python
from flask import Flask, render_template, request
app = Flask(__name__) #변수에 저장

@app.route("/") 
def hello():
    return "Hello World!"

```

> app.route : 라우트는 경로를 받아주는 것
>
> hello()라는 함수를 만들고 "Hello world!"라는 문자열을 반환한다.

- greeting이라는 루트 뒤에 이름을 입력하여 이름 출력하기
``` python 
@app.route('/greeting/<string:name>')
def greeting(name):
    return f'안녕하세요 {name}님!'
```
>@app.route을 통해 값을 받고 함수 greeting의 매개변수로 받아 이름과 함께 인삿말을 반환시킨다.

- 위와 동일하지만 render_template을 이용하여 greeting.html에서 문자 반환하는 코드

- render_template() 함수를 사용해서 HTML 파일을 랜더링

``` python
@app.route("/greeting_html/<string:name>")
def greeting_html(name):
        return render_template('greeting.html', name = name)           
```
>render_template을 통해 greeting.html과 연결되고 변수 name 에 이름 값을 저장하고 이를 greeting.html에서 보여주게 한다.

- 점심 메뉴를 lunch.html에서 사진과 이름 보여주기
``` python 
import random
@app.route('/lunch')
def lunch():
    menu = {
        '짜장면' : 'http://cdnweb01.wikitree.co.kr/webdata/editor/201704/13/img_20170413122520_54eea70d.jpg',
        '짬뽕' : 'https://upload.wikimedia.org/wikipedia/commons/b/bb/Jjamppong.jpg',
        '스파게티' : 'https://t1.daumcdn.net/cfile/tistory/203BDF3E4E9D975D36',
    }

    menu_list = list(menu.keys())
    pick = random.choice(menu_list)
    img = menu[pick]

    return render_template('lunch.html',pick =pick, img= img)
```
>함수 lunch에 menu 라는 음식이름을 키로 사진을 값으로 하는 딕셔너리를 생성합니다. 
>
>menu_list에 키 값만 모은 정보들을 리스트로 만들어 저장한다.
>
>menu_list에서 random.choice를 통해서 하나의 메뉴를 선택하고 딕셔너리의 키를 이용하여 사진을 얻는다.
>
>이러한 결과물을 각각 render_template을 통해서 변수를 할당하고 랜덤한 점심메뉴 결과물을 얻는다.



- vonvon이라는 페이지에서 이름을 입력하면 past라는 페이지에서 랜덤한 결과물을 얻게 하는 코드
``` python 
@app.route('/vonvon')
def vonvon():
    return render_template('vonvon.html')

@app.route('/past')
def past():
    lastlife = {
        '소작농' : 'https://comps.canstockphoto.co.kr/%EB%86%8D%EC%9B%90-%EC%8C%80-%EC%9D%BC-%EC%95%84%EC%8B%9C%EC%95%84-%EC%82%AC%EB%9E%8C-%EC%86%8C%EC%9E%91%EB%86%8D-eps-%EB%B2%A1%ED%84%B0_csp17940289.jpg',
        '선비' : 'https://pbs.twimg.com/profile_images/876705561395421184/Qt79Cten_400x400.jpg',
        '중전' : 'http://imgmaak.petaz.co.kr/maak-bucket/content/20170201015414-UbTHH.jpg',
        '고양이' : 'http://img.hani.co.kr/imgdb/resize/2018/0313/00500561_20180313.JPG',
        '부자' : 'https://img-s-msn-com.akamaized.net/tenant/amp/entityid/BBWkUA6.img?h=233&w=559&m=6&q=60&o=f&l=f&x=296&y=87'

    }

    life_list = list(lastlife.keys())
    pick = random.choice(life_list)
    img = lastlife[pick]

    return render_template('past.html', pick = pick, img=img)
```
```html
    <form action="/past"> 
        <input type="text" name = 'name'>
        <input type="submit">
    </form>
```

> 입력창에 이름을 입력하면 submit이라는 타입을 가진 입력태그를 클릭하면 form태그의 action으로 인해 past라는 페이지로 이동하게 된다. 

- 로또 결과를 입력한 결과와 비교하면 등수 확인하기
``` python

@app.route('/lotto')
def lotto():
    return render_template('lotto.html')

@app.route('/lotto_result')
def lotto_result():
    #사용자가 입력한 정보를 가져오기
    numbers = request.args.get('numbers').split()
    user_numbers = []

    for n in numbers :
        user_numbers.append(int(n)) #사용자의 입력정보 리스트로 저장
    #로또 홈페이지에서 정보를 가져오기
    url = "https://www.dhlottery.co.kr/common.do?method=getLottoNumber&drwNo=866"
    res = requests.get(url)
    lotto_numbers = res.json() #스트링인 타입을 딕셔너리 타입으로 변화시켜줌

    winning_numbers =[] 
    for i in range(1,7) :
        winning_numbers.append(lotto_numbers[f'drwtNo{i}'])
        #기존의 우승 넘버 목록의 데이터를 가져와 리스트에 저장
    bonus_number = [lotto_numbers['bnusNo']]
    #보너스 넘버를 set함수로 사용하기 위해서 리스트로 만듬
	


    matched = len(set(user_numbers) & set(winning_numbers))
    #set함수에서 &를 통해 교집합의 결과를 생성하고 그 수 만큼의 길이를 저장
    if matched == 6 : #만약 6개 맞으면 1등
        result = '1등'
    elif matched  == 5 :#만약 5개 맞으면서 보너스 점수도 있으면
        if len(set(user_numbers) & set(bonus_number)) ==1 : 
            result = '2등' #없으면 2등
        else : #있으면 3등
            result = '3등'
    elif matched == 4 :
        result = '4등'
    elif matched == 3 :
        result = '5등'
    else :
        result = '꽝'
    return render_template('lotto_result.html', u = user_numbers, w = winning_numbers, b = bonus_number, r = result)
    #이를 lotto_result.html에 보여주기
```
