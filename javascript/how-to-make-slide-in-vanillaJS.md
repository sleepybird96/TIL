# Solo week sprint Part2-2 slide and Part2-3 sliding menu
 솔로위크를 더 알차게 보내기 위해  
__코드스테이츠 최강 듀오 지상, 상권 합쳐서 지상권이 자체 스프린트를 진행한다!__  

  
__깃헙 레포지토리__ : https://github.com/sleepybird96/solo-week-sprint-vanillaJS  
__코공(이상권)블로그__ : https://velog.io/@rnrel11

___  
# 바닐라JS로 슬라이드창 만들기  
슬라이드 효과는 자바스크립트로 웹사이트를 역동적으로 표현하기 위해서라면,  
필수적으로 알아야 할 효과이다.  
다소 역동적인 부분이 있기에 배우기 이전에 겁을 먹었으나,  
생각보다 __원리는 간단했다.__  
천천히, 그리고 재밌게 알아보자.  
## 슬라이드창의 구조  

<a href="https://imgur.com/60eGPe2"><img src="https://i.imgur.com/60eGPe2.png" title="source: imgur.com" /></a>

위와 같은데, 포인트는 __각각의 이미지가움직이는게 아닌__  
__슬라이드 필름이 움직이는 것이다.__  
좌우 슬라이드라면 __x축으로 움직이고,__  
상하 슬라이드라면 __y축으로 움직인다.__  
  
### 좌 우 버튼이 있다고 가정했을 때 수도코드  
```
현재 페이지를 변수로 선언해주고 초기값을 1로 할당해준다.  
좌측 버튼을 눌렀을 때,
  페이지는 1 감소한다.
  x축으로 (페이지 - 1) * 이미지의 넓이만큼 슬라이드 필름을 움직인다.
우측 버튼을 눌렀을 때,
  페이지는 1 증가한다.
  x축으로 (페이지 - 1) * 이미지의 넓이만큼 슬라이드 필름을 움직인다.
```  
여기서 문제점이 있다. 이미지가 없을 때도  
x축의 음수만큼 혹은 양수만큼 __무한히 저편으로 사라질 것이다.__  

그래서 조건을 걸어주자.  
마지막 이미지에서 __우측을 누르면 첫번째 이미지로__  
첫번째 이미지에서 __좌측을 누르면 마지막 이미지로__  
이동할 수 있게 조건문을 추가한다.  
방법은 간단하다. 따로 슬라이드를 이동해줄 필요없이,  
페이지만 조정해주자.
```
현재 페이지를 변수로 선언해주고 초기값을 1로 할당해준다.  
좌측 버튼을 눌렀을 때,
  페이지는 1 감소한다.
  (만약 페이지가 1보다 작으면 )
  {페이지에 3을 할당한다.}
  x축으로 (페이지 - 1) * 이미지의 넓이만큼 슬라이드 필름을 움직인다.
우측 버튼을 눌렀을 때,
  페이지는 1 증가한다.
  (만약 페이지가 이미지의 갯수보다 크면)
  {페이지에 1을 할당한다.}
  x축으로 (페이지 - 1) * 이미지의 넓이만큼 슬라이드 필름을 움직인다.
```  
  
우측으로 눌렀을 때 첫페이지로 작위적으로 움직이는게 싫다면,  
opacity를 활용해  
__마지막페이지에서 투명해지고 첫번째 페이지에서 다시 나타나게__ 할 수 있다.  
더 알아보고 싶다면 mdn에서 transition효과에 대해 알아보고,  
opacity를 __언제 1로 주고 언제 0으로 줘야할지 각자 생각해보자__  
구조와 수도코드를 알았다면, 위 구조를 토대로 슬라이드 창을 만들어보자.  

<p class="codepen" data-height="265" data-theme-id="light" data-default-tab="js,result" data-user="sleepybird96" data-slug-hash="gOwppZd" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="gOwppZd">
  <span>See the Pen <a href="https://codepen.io/sleepybird96/pen/gOwppZd">
  gOwppZd</a> by Jisang Park (<a href="https://codepen.io/sleepybird96">@sleepybird96</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>  

## HTML key POINT  
이미지를 감싸는 필름역할을 해줄 엘리먼트가 있어야되고,  
그 필름을 감싸는 슬라이드 영역이 있어야 한다.  
  
## CSS key POINT  
슬라이드 필름에 __transition을 원하는 지속시간만큼 달아준다.__  
그리고 슬라이드를 보여주는 상자에는 __overflow: hidden__  
슬라이드 필름에는 __오버플로우 값을 주지않도록 주의하자__  
  
## javascript key POINT  
위 수도코드를 참고하자.  
스타일에 transform을 줘야하는데, 구글에 transform mdn을 검색해보자.  
  
___  
# 슬라이딩하는 메뉴창 만들기  
메뉴창을 슬라이드효과를 주며 등장하게 만들어 보자.  
위 슬라이드 개념을 이해했다면, 쉽게 이해할 수 있다.  
  
## 수도코드  
```
메뉴창을 누르면  
  메뉴 버튼은 사라진다.  
  body바깥에 있던 메뉴를 x축만큼 재등장 시킨다.  
메뉴창에서 닫기 버튼을 누르면  
  메뉴버튼이 다시 나온다.  
  body바깥으로 메뉴창을 밀어낸다.
```
### 코드펜으로 확인하기  

<p class="codepen" data-height="265" data-theme-id="light" data-default-tab="css,result" data-user="sleepybird96" data-slug-hash="YzGXymo" style="height: 265px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;" data-pen-title="Slide Menu in vanillaJS">
  <span>See the Pen <a href="https://codepen.io/sleepybird96/pen/YzGXymo">
  Slide Menu in vanillaJS</a> by Jisang Park (<a href="https://codepen.io/sleepybird96">@sleepybird96</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

### 코드펜 불러오기에서 깨집니다 코드펜 우측상단 editon codepen 버튼 누르시고 확인하세요!

___ 
이전편: https://sleepybird.tistory.com/123  
코공(이상권)슬라이드 정리글 보기: https://velog.io/@rnrel11/TIL-34%EC%9D%BC%EC%B0%A8-%EC%A1%B8%EB%A6%B0%EC%83%88x%EC%BD%94%EA%B3%B5-%EC%8A%AC%EB%9D%BC%EC%9D%B4%EB%93%9C-%EA%B5%AC%ED%98%84