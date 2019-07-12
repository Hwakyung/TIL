# StartCamp day04


### .env 확장 파일

- 독립적인 가상 실행환경으로 다수의 패키지 설치로 인한 충돌을 방지해주기도 한다.
 
### python-decouple

- python-decouple 패키지는 env설정 파일을 파싱해줄 수 있게 해준다.

### Webhook

- 웹훅은 새 이벤트 (클라이언트 측 응용 프로그램이 관심을 가질 수있는)가 서버에서 발생한 경우 서버 측 응용 프로그램이 클라이언트 측 응용 프로그램에 알릴 수있는 메커니즘을 제공한다.
- 웹훅은 텔레그램에게 어떤 정보를 보낼 것인지 경로를 알려준다..

### requests 모듈의 POST

- POST: 웹의 주소는 요청을 보내는 것으로 매개변수를 통해 쉽게 통신할 수 있다.
> get : 가져가는 것
> post : 주문
> update : 리필
> delete : 반납

### 플라스크를 통해서 텔레그램 챗봇 만들기

``` python 
from flask import Flask, request, render_template
from decouple import config
import requests
import random
from bs4 import BeautifulSoup

app = Flask(__name__)

api_url = 'https://api.telegram.org'
token = config('TELEGRAM_TOKEN') # 가상실행환경에 토큰을 저장, 보안의 문제 
chat_id = config('CHAT_ID')
naver_id = config('NAVER_ID')
naver_secret = config('NAVER_SECRET')


@app.route('/write')
def write():
    return render_template("write.html")

@app.route('/send')
def send():
    msg = request.args.get('msg')
    url = f"{api_url}/bot{token}/sendMessage?chat_id={chat_id}&text={msg}"
    res = requests.get(url)
    return render_template("send.html")
#사용자가 메세지를 입력하면 send.html으로 보내게한다.

@app.route(f"/{token}", methods = ['POST']) #서버로 요청이 들어왔다는 것
def telegram():
    print(request.get_json())
    data = request.get_json()
    #.json()으로 json을 파일을 딕셔너리 형태로 읽을 수 있게 해줌
    user_id = data.get('message').get('from').get('id') #누가 내 텔레그램에 메세지를 보내는지 확인
    user_msg = data.get('message').get('text') 
    #어떤 메세지를 보냈는지 확인 
    
    if data.get('message').get('photo') is None:
	#만약 message의 photo가 없다면
        if user_msg == '점심메뉴':
            menu_list =['삼계탕','철판낙지볶음밥','물냉면']
            result = random.choice(menu_list)
            #점심메뉴를 입력했을 때, 리스트에서 랜덤으로 하나 뽑기
        elif user_msg == '로또':
            numbers = list(range(1,46))
            result = sorted(random.sample(numbers,6))
            #로또 번호를 뽑기
        elif user_msg == '미세먼지' :
            url = 'https://search.naver.com/search.naver?where=nexearch&sm=tab_etc&query=%EA%B4%91%EC%A3%BC%20%EA%B4%91%EC%82%B0%EA%B5%AC%20%EB%AF%B8%EC%84%B8%EB%A8%BC%EC%A7%80'
            res = requests.get(url).text
            soup = BeautifulSoup(res, 'html.parser')
            dust = soup.select_one('.main_figure').text
            
            #미세먼지 HTTP데이터를 크롤링하여 데이터를 얻고 dust에 저장
            
            if int(dust) > 75 :
                result = f"현재 수치는 {dust}이며 매우 나쁨입니다."
            elif int(dust) > 35 :
                result = f"현재 수치는 {dust}이며 나쁨입니다."
            elif int(dust) > 15 :
                result = f"현재 수치는 {dust}이며 보통입니다."
            else :
                result = f"현재 수치는 {dust}이며 좋음입니다."
        elif user_msg == '실시간' :
            url = 'https://www.naver.com/'
            res = requests.get(url).text
            soup = BeautifulSoup(res, 'html.parser')
            naver = soup.select_one('.ah_k').text
            result = f"지금 실시간 검색어 1위는 `{naver}`입니다."
            #네이버 검색어 크롤링하기
        elif user_msg == '커피추천' :
            coffee = ['아메리카노','카페라떼','헤이즐넛라떼','아인슈페너','플랫화이트','캬라멜마끼아또','바닐라라떼','카페모카']
            select= random.choice(coffee)
            result = f'오늘은 {select} 어떨까요?'
        elif user_msg[0:2] == "번역":
        	#번역이라는 글자가 있으면 
            raw_text = user_msg[3:] #번역할 글자를 raw_text에 저장하고
            papago_url = 'https://openapi.naver.com/v1/papago/n2mt'
            data = {
                "source" : 'ko',
                "target" : "en",
                "text": raw_text
            }
            #파파고 url를 가져와 data 딕셔너리에 저장한다
            header = {
                "X-Naver-Client-Id" : naver_id,
                "X-Naver-Client-Secret" : naver_secret
            }
            res = requests.post(papago_url,data = data, headers = header) #post를 통해서 파파고url과 데이터 및 클라이언트 아이디 등을 입력
            
            translate_res = res.json() # json()으로 변환
            translate_result = translate_res.get('message').get('result').get('translatedText')
            result = translate_result
            #파파고에서 번역된 결과물을 가져와 result 변수에 저장
        # elif user_msg == '브런치' :
        #     url ='https://brunch.co.kr/'
        #     res = requests.get(url).text
        #     soup = BeautifulSoup(res, 'html.parser')
        #     article = soup.select_one('#mArticle > div.editor_pic > div.wrap_slide > ul > li:nth-child(1) > div > div.item_pic.item_pic_type2 > a')
        #     print(article)
        #     result = 'ok'
        else : 
            result = user_msg
    else :
        #사용자가 보낸 사진을 찾는 과정
        result = '사진 보내기'
        file_id = data.get('message').get("photo")[-1].get('file_id')
        file_url = f"{api_url}/bot{token}/getFile?file_id={file_id}"
        file_res = requests.get(file_url)
        file_path = file_res.json().get('result').get('file_path')
        file = f"{api_url}/file/bot{token}/{file_path}"
        print(file)

        #사용자가 보낸 사진을 클로버로 전송
        res = requests.get(file, stream = True)
        clova_url = "https://openapi.naver.com/v1/vision/celebrity"
        header = {
            "X-Naver-Client-Id" : naver_id,
            "X-Naver-Client-Secret" : naver_secret

        }
        clova_res = requests.post(clova_url, headers = header, files = {'image' :res.raw.read()})
        
        if clova_res.json().get('info').get('faceCount') :
            #누구랑 닮았는지 출력
            celebrity = clova_res.json().get('faces')[0].get('celebrity')
            print(celebrity)
            name = celebrity.get('value')
            confidence = celebrity.get('confidence')
            result = f"{name}일 확률이 {confidence*100}%입니다."
        else :
            #사람이 없음
            result = '사람이 없습니다.'


    res_url = f"{api_url}/bot{token}/sendMessage?chat_id={user_id}&text={result}" 
    requests.get(res_url) #챗봇이 메아리 치는 것
    return '', 200


if __name__ == '__main__':
    app.run(debug=True)
```