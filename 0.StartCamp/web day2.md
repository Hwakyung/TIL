# web day02

- CSS란? 
  -	CSS는 Cascading Style Sheets의 약자로 스타일 시트 언어임
- color
  - background-color: 배경의 컬러를 부여해줄 수 있음
  - color :글씨의 색깔을 넣어줄 수 있음
- font
  - font-family: 글씨체를 변경할 수 있으며 goolge fonts를 통해서 다른 글씨체를 가져올 수 있음
- box model
  - 문서의 레이아웃을 계산할 때,  CSS 기본 박스 모델에 따라 각각의 요소를 사각형 박스로 표현
  - 1. 콘텐츠 영역은 글이나 이미지, 비디오 등 요소의 실제 내용을 포함
       - [`width`](https://developer.mozilla.org/ko/docs/Web/CSS/width), [`min-width`](https://developer.mozilla.org/ko/docs/Web/CSS/min-width), [`max-width`](https://developer.mozilla.org/ko/docs/Web/CSS/max-width), [`height`](https://developer.mozilla.org/ko/docs/Web/CSS/height), [`min-height`](https://developer.mozilla.org/ko/docs/Web/CSS/min-height), [`max-height`]으로 조절함
    2. 패딩 영역은 콘테츠 영역을 요소의 안쪽 여백까지 포함하는 크기로 확장
       - [`padding-top`](https://developer.mozilla.org/ko/docs/Web/CSS/padding-top), [`padding-right`](https://developer.mozilla.org/ko/docs/Web/CSS/padding-right), [`padding-bottom`](https://developer.mozilla.org/ko/docs/Web/CSS/padding-bottom), [`padding-left`]와 단축속성 padding으로 결정
    3. 테두리 영역은 안쪽 여백 영역을 요소의 테두리까지 포함 
       -  [`border-width`](https://developer.mozilla.org/ko/docs/Web/CSS/border-width)와 단축 속성인 [`border`](https://developer.mozilla.org/ko/docs/Web/CSS/border)가 결정
       - .[`box-sizing`] 속성의 값이 `border-box`라면 테두리 영역의 크기를 [`width`](https://developer.mozilla.org/ko/docs/Web/CSS/width), [`min-width`](https://developer.mozilla.org/ko/docs/Web/CSS/min-width), [`max-width`](https://developer.mozilla.org/ko/docs/Web/CSS/max-width), [`height`](https://developer.mozilla.org/ko/docs/Web/CSS/height), [`min-height`](https://developer.mozilla.org/ko/docs/Web/CSS/min-height), [`max-height`](https://developer.mozilla.org/ko/docs/Web/CSS/max-height) 속성을 사용해 명시적으로 설정
    4. 바깥 여백 영역은 테두리 요소를 확장해 요소와 인근 요소 사이의 빈 공간까지 포함하도록 만듬
       - [`margin-top`](https://developer.mozilla.org/ko/docs/Web/CSS/margin-top), [`margin-right`](https://developer.mozilla.org/ko/docs/Web/CSS/margin-right), [`margin-bottom`](https://developer.mozilla.org/ko/docs/Web/CSS/margin-bottom), [`margin-left`](https://developer.mozilla.org/ko/docs/Web/CSS/margin-left)와 단축 속성인 [`margin`](https://developer.mozilla.org/ko/docs/Web/CSS/margin)이 결정
- position : 문서상에 요소를 배치하는 방법으로  [`top`](https://developer.mozilla.org/ko/docs/Web/CSS/top), [`right`](https://developer.mozilla.org/ko/docs/Web/CSS/right), [`bottom`](https://developer.mozilla.org/ko/docs/Web/CSS/bottom),  [`left`](https://developer.mozilla.org/ko/docs/Web/CSS/left) 속성이 요소를 배치할 최종 위치를 결정
  - 배치유형
    - relative : 상대적 배치 요소로 top과 bottom은 원래 위치에서의 세로축 거리를 left와 right은 원래 위치에서의 가로축 거리 지정
    - absolute :절대적 배치 요소로 [`top`](https://developer.mozilla.org/ko/docs/Web/CSS/top), [`right`](https://developer.mozilla.org/ko/docs/Web/CSS/right), [`bottom`](https://developer.mozilla.org/ko/docs/Web/CSS/bottom), [`left`](https://developer.mozilla.org/ko/docs/Web/CSS/left)는 요소 [컨테이닝 블록](https://developer.mozilla.org/ko/docs/Web/CSS/All_About_The_Containing_Block) 모서리로부터의 거리를 지정
    - fixed : 절대적 배치 요소로 [`top`](https://developer.mozilla.org/ko/docs/Web/CSS/top), [`right`](https://developer.mozilla.org/ko/docs/Web/CSS/right), [`bottom`](https://developer.mozilla.org/ko/docs/Web/CSS/bottom), [`left`](https://developer.mozilla.org/ko/docs/Web/CSS/left)는 요소 [컨테이닝 블록](https://developer.mozilla.org/ko/docs/Web/CSS/All_About_The_Containing_Block) 모서리로부터의 거리를 지정
    - sticky: `position`의 [계산값](https://developer.mozilla.org/ko/docs/Web/CSS/computed_value)이 `sticky`인 요소



