# web day01

 요청의 종류 1. 줘라(get) 2.받아라(post)

### static web 

- 서버에 미리 저장된 파일이 그대로 전달되는 웹 페이지 

### dynamic web
- 서버에 있는 데이터들을 스크립트에 의해 가공처리한 후 생성되어 전달되는 웹 페이지

- web의 구성
  - IP(internet Protocol) :8비트까지의 숫자로 구성된 숫자의 집합으로, 각자가 가지고 있는 주소와 동일함.

  - 도메인(Domain) : 네트워크 상의 컴퓨터를 식별하는 호스트명

  - URL(Uniform Resource Locator) : 도메인 + 경로, 실제로 해당 서버에 저장된 자료의 위치

### Hyper Text Markup Language

- Hyper Text: 모든 문서들을 경로을 타고 들어갈 수 있는 것
	- Hyper Text Transfer Protocol : HTTP(S) 규칙을 통해서 문서를 전해주는 것

- Markup : 문서를 구조화하는 것 
- Language : 규칙



주석 : html문서가 읽지 않음 

<!-- -->

- 속성(attribute)  :태그에는 속성이 지정될 수 있음 

``` html
<a href ="google.com"/> 속성명 속성값
""을 쓰는 것을 권장함
```



- element : 여는 태그와 닫는 태그로 구성되어있음

- DOM트리 : 원도우 탐색기의 파일 구조와 같은 것임

- 시맨틱태그 :  공간자체에 외의 의미가 없음 검색엔진 봤을 때, tab들을 컴퓨터가 알아 볼 수 있게 만드는 것

``` html
<h1>
    
</h1>
<h2>
    
</h2>
```

- p태그:본문을 쓰는 곳
- strong 의미가 있고 b태그는 의미가 없다는 것

self-closing element :닫는 태그가 없는 태그도 존재

``` html
<ol>
    <li></li>
    <li></li>
</ol>

<a href="https://naver.com">네이버</a> 하이퍼텍스트를 보내주는 태그
```

- html  문서 만들기

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
    <h1>프로그래밍 교육</h1>
    <a href="#python"><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/c/c3/Python-logo-notext.svg/768px-Python-logo-notext.svg.png" width="50" height="50"></a>
    <a href="#web"><img src="./images/html.png" width="50" height="50"></a>
    <a href="intro.html">참고사이트</a>
    <hr>
    <div>
        <h2 id="python"><a href="https://docs.python.org/ko/3/tutorial/index.html" target="_blank" >파이썬</a></h2>
        <h3>Number type</h3>
        <p>파이썬에서 숫자형은 아래와 같이 있다.</p>
        <ol>
            <!--ordered lists를 작성할 수 있게 해주는 태그-->
            <li>int</li>
            <li>float</li>
            <li>complex</li>
            <li><del>str</del></li>  
        </ol>

        <h3>Sequence</h3>
        <p>파이썬에서 시퀀스는 아래와 같이 있다.</p>
        <p><b>시퀀스는 for문을 돌릴 수 있다.</b></p>
        <ol>
            <li>str</li>
            <li>list</li>
            <li>tuple</li>
            <li>range</li>  
        </ol>
    </div>

    <hr>
	 <!--수직선을 생성하는 태그-->
    <div>
        <h2 id="web"><a href="https://developer.mozilla.org/ko/" target="_blank">웹</a></h2>

        <h3>기초</h3>
        <ul>
            <li style="list-style: circle">HTML</li>
            <li style="list-style: circle">CSS</li>
        </ul>
    </div>
</body>
</html>
```

- 표 만들기
``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>

      table, th, td {
        border: 1px solid #bcbcbc;
        text-align: center;
      }
    </style>
</head>
<body>
    <table>  
<!-- 테이블을 만드는 코드-->     
        <thead>
            <!--표의 가장 위에 부분-->   
            <tr>
                <th></th>
                <th>월</th>
                <th>화</th>
                <th>수</th>
            </tr>
        </thead>
        <tbody>
            <!--표의 내용을 작성하는 곳-->   
            <tr>
                <th>A코스</th>
                <td rowspan="2">짬뽕</td>
                <!-- rowspan 세로줄을 합해주는 것-->     
                <td colspan="2">초밥</td>
                <!-- colspan 가로줄을 합해주는 것-->    
            </tr>
            <tr>
                <th>B코스</th>
                <td>김치찌개</td>
                <td>삼계탕</td>
            </tr>
        </tbody>
    </table>
</body>
</html>
```





