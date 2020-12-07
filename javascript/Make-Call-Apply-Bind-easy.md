# javascript bind call apply 5분만에 이해하기  
필자는 call 과 apply 그리고 bind를 이해하는데 꽤나 애먹었다.  
왜냐면 세개를 각기 달리 하고 따로따로 이해하려고 했기때문이다.  
하지만 __셋의 개념을 동시에 비교하며 사용해본다면 무척이나 쉬울것이다.__  
이 지구에서 셋을 가장 쉽게 설명했다고 자신할 수 있다.
___  
# bind는 함수를 리턴하고 call과 apply는 함수를 실행한다.  
세 친구의 첫번째 인자인 this는 일단 무시하고  
얘네가 뭘하는 친구인지 정도는 알자  
__bind는 함수를 실행못하게 묶는다. 그저 함수를 퉤뱉는다__  
__call과 apply는 함수를 실행한다__  

왜 반복해서 말하냐면,  
사실 이게 절반이기 때문이다. 나머지 절반은 안에들어가는 this에대해 이해하면 끝  
## 사용해보자!  

<div class="colorscripter-code" style="color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#272727;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #4f4f4f"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#aaa;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div><div style="line-height:130%">3</div><div style="line-height:130%">4</div><div style="line-height:130%">5</div><div style="line-height:130%">6</div><div style="line-height:130%">7</div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">function</span>&nbsp;Hello&nbsp;(<span style="color:#4be6fa">name</span>){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#4be6fa">console</span>.log(<span style="color:#ffd500">'Hello&nbsp;from'</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#4be6fa">console</span>.log(<span style="color:#4be6fa">this</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#ff3399">if</span>(<span style="color:#4be6fa">name</span>){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#4be6fa">console</span>.log(`My&nbsp;<span style="color:#4be6fa">name</span>&nbsp;is&nbsp;${<span style="color:#4be6fa">name</span>}`)</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">}</div></div><div style="text-align:right;margin-top:-13px;margin-right:5px;font-size:9px;font-style:italic"><a href="http://colorscripter.com/info#e" target="_blank" style="color:#4f4f4ftext-decoration:none">Colored by Color Scripter</a></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none;color:white"><span style="font-size:9px;word-break:normal;background-color:#4f4f4f;color:white;border-radius:10px;padding:1px">cs</span></a></td></tr></table></div>

당장 구글 개발자창을 열어라,  
그리고 위 함수를 만들고 실행시키자.  

## 그냥 실행시켰을 때  
<a href="https://imgur.com/AyXgc2s"><img src="https://i.imgur.com/AyXgc2s.png" title="source: imgur.com" /></a>  

## bind로 묶었을때  
<a href="https://imgur.com/3sqJLR5"><img src="https://i.imgur.com/3sqJLR5.png" title="source: imgur.com" /></a>  
__함수를 퉤 뱉는다__  
## call과 apply로 실행시켰을 때  
<a href="https://imgur.com/FeeAOn2"><img src="https://i.imgur.com/FeeAOn2.png" title="source: imgur.com" /></a>  
<a href="https://imgur.com/m3BtiTU"><img src="https://i.imgur.com/m3BtiTU.png" title="source: imgur.com" /></a>  
__그냥 함수를 실행시킨것과 다름없다.__  

___  
# 셋 다 함수안의 this값을 3형제의 첫번 째 인자가 정한다.  
전혀 어려운 소리가 아니다.  
__bind call apply 3형제를 쓸땐,__  
함수안의 __this를 그저 함수안의 매개변수로 생각해라__  
## 사용해보자!  
예제는 똑같지롱  
<div class="colorscripter-code" style="color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#272727;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #4f4f4f"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#aaa;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div><div style="line-height:130%">3</div><div style="line-height:130%">4</div><div style="line-height:130%">5</div><div style="line-height:130%">6</div><div style="line-height:130%">7</div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">function</span>&nbsp;Hello&nbsp;(<span style="color:#4be6fa">name</span>){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#4be6fa">console</span>.log(<span style="color:#ffd500">'Hello&nbsp;from'</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#4be6fa">console</span>.log(<span style="color:#4be6fa">this</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#ff3399">if</span>(<span style="color:#4be6fa">name</span>){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#4be6fa">console</span>.log(`My&nbsp;<span style="color:#4be6fa">name</span>&nbsp;is&nbsp;${<span style="color:#4be6fa">name</span>}`)</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">}</div></div><div style="text-align:right;margin-top:-13px;margin-right:5px;font-size:9px;font-style:italic"><a href="http://colorscripter.com/info#e" target="_blank" style="color:#4f4f4ftext-decoration:none">Colored by Color Scripter</a></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none;color:white"><span style="font-size:9px;word-break:normal;background-color:#4f4f4f;color:white;border-radius:10px;padding:1px">cs</span></a></td></tr></table></div>  

예제는 똑같다 사용해보아라!  
## bind의 첫번째 인자로 this를 정해줬을 때  
<a href="https://imgur.com/cNuAqaT"><img src="https://i.imgur.com/cNuAqaT.png" title="source: imgur.com" /></a>  

### 사실얘는 함수만 퉤 뱉기 때문에 별다른 차이를 모른다.  
### 그런데 __bind도 실행시킴으로써 속박을 풀수있다__ 뒤에()를입력하자.  
<a href="https://imgur.com/VbIWpc9"><img src="https://i.imgur.com/VbIWpc9.png" title="source: imgur.com" /></a>  

### __포인트는 함수 안 this에 bind의 인자가 들어간것!__  
  
</br>

### mdn에 첫번 째 인자로 this가 들어간다고 해서 __객체만 들어갈 줄 알았는데__  
### 아니다!  
### 보다시피 __문자열 , number 다 된다!__  
### 그래서 __이 셋(콜,어플라이,바인드)을 만난다면 this를 그저 매개변수로 생각해라!__  

## call과 apply의 첫번 째 인자로 this를 정해주고 각각 실행  
<a href="https://imgur.com/z0LApPV"><img src="https://i.imgur.com/z0LApPV.png" title="source: imgur.com" /></a>  

<a href="https://imgur.com/4fjFAdx"><img src="https://i.imgur.com/4fjFAdx.png" title="source: imgur.com" /></a>  

### __Hello.bind('우리집')() 과 똑같다__  

___  
# 3형제의의 두번째 인자부터 함수의 인자가 들어간다.  
여기서 주의점이 있다.  
__apply만 인자를 배열에 집합시켜서 넣는다!__  
## 사용해보자!  
예제는 똑같지롱  
<div class="colorscripter-code" style="color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#272727;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #4f4f4f"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#aaa;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div><div style="line-height:130%">3</div><div style="line-height:130%">4</div><div style="line-height:130%">5</div><div style="line-height:130%">6</div><div style="line-height:130%">7</div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">function</span>&nbsp;Hello&nbsp;(<span style="color:#4be6fa">name</span>){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#4be6fa">console</span>.log(<span style="color:#ffd500">'Hello&nbsp;from'</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#4be6fa">console</span>.log(<span style="color:#4be6fa">this</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#ff3399">if</span>(<span style="color:#4be6fa">name</span>){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#4be6fa">console</span>.log(`My&nbsp;<span style="color:#4be6fa">name</span>&nbsp;is&nbsp;${<span style="color:#4be6fa">name</span>}`)</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">}</div></div><div style="text-align:right;margin-top:-13px;margin-right:5px;font-size:9px;font-style:italic"><a href="http://colorscripter.com/info#e" target="_blank" style="color:#4f4f4ftext-decoration:none">Colored by Color Scripter</a></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none;color:white"><span style="font-size:9px;word-break:normal;background-color:#4f4f4f;color:white;border-radius:10px;padding:1px">cs</span></a></td></tr></table></div>  

예제는 똑같다 사용해보아라!  
## call과 bind의 두번째 인자부터 함수의 인자가 들어감!  

<a href="https://imgur.com/ANF94M3"><img src="https://i.imgur.com/ANF94M3.png" title="source: imgur.com" /></a>  

### __주의!__ bind를 실행시켜 속박을 푼것이다!  
### 인자를 넣어주지만 속박을 안풀면 뱉는건 __인자를 미리 넣은함수__
<a href="https://imgur.com/TKaBGXd"><img src="https://i.imgur.com/TKaBGXd.png" title="source: imgur.com" /></a>  

### call은 그런거 걱정말고 쓰자.  

### __여기서 깜짝 퀴즈!__  
### 적용할 함수의 두번째 인자는 call과 bind의 몇번째 인자일까용~?  

</br>
</br>
</br>

### __정답은__ 각각의 세번째 인자다!
<div class="colorscripter-code" style="color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#272727;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #4f4f4f"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#aaa;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div><div style="line-height:130%">3</div><div style="line-height:130%">4</div><div style="line-height:130%">5</div><div style="line-height:130%">6</div><div style="line-height:130%">7</div><div style="line-height:130%">8</div><div style="line-height:130%">9</div><div style="line-height:130%">10</div><div style="line-height:130%">11</div><div style="line-height:130%">12</div><div style="line-height:130%">13</div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">function</span>&nbsp;add&nbsp;(a,&nbsp;b){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#ff3399">return</span>&nbsp;<span style="color:#4be6fa">this</span>&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">+</span>&nbsp;(a&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">+</span>&nbsp;b);</div><div style="padding:0 6px; white-space:pre; line-height:130%">}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#999999">//각각&nbsp;따로&nbsp;엔터해보자</span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#999999">//엔터&nbsp;1</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">add.bind(<span style="color:#ffd500">'정답은'</span>,&nbsp;<span style="color:#c10aff">1</span>,&nbsp;<span style="color:#c10aff">5</span>)()</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#999999">//엔터&nbsp;2</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">add.call(<span style="color:#ffd500">'정답은'</span>,&nbsp;<span style="color:#c10aff">1</span>,&nbsp;<span style="color:#c10aff">5</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#999999">//엔터&nbsp;3</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">add.bind(<span style="color:#c10aff">5</span>,&nbsp;<span style="color:#c10aff">3</span>,&nbsp;<span style="color:#c10aff">2</span>)()</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#999999">//엔터&nbsp;4</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">add.call(<span style="color:#c10aff">5</span>,&nbsp;<span style="color:#c10aff">3</span>,&nbsp;<span style="color:#c10aff">2</span>)</div></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none;color:white"><span style="font-size:9px;word-break:normal;background-color:#4f4f4f;color:white;border-radius:10px;padding:1px">cs</span></a></td></tr></table></div>  
각각 시도해보자  
<a href="https://imgur.com/bg0tyEz"><img src="https://i.imgur.com/bg0tyEz.png" title="source: imgur.com" /></a>  
<a href="https://imgur.com/PEpsSxK"><img src="https://i.imgur.com/PEpsSxK.png" title="source: imgur.com" /></a>

## apply는 두번째 인자부터 __인자를 집합시킨 배열을 함수에 적용한다.__  
인자가 단 하나라도 말이다!  
무조건 __배열에 집합시킨 인자를 받는다!__  
<a href="https://imgur.com/BDQgg8E"><img src="https://i.imgur.com/BDQgg8E.png" title="source: imgur.com" /></a>  
배열에 집합안시키니까 싫어하는것좀 봐라.  
__인자가 한개라도 배열에 집합시켜서 던져주자__  
<a href="https://imgur.com/qvEghYB"><img src="https://i.imgur.com/qvEghYB.png" title="source: imgur.com" /></a>  
  

### __예제 2__
<div class="colorscripter-code" style="color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#272727;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #4f4f4f"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#aaa;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div><div style="line-height:130%">3</div><div style="line-height:130%">4</div><div style="line-height:130%">5</div><div style="line-height:130%">6</div><div style="line-height:130%">7</div><div style="line-height:130%">8</div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">function</span>&nbsp;add&nbsp;(a,&nbsp;b){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#ff3399">return</span>&nbsp;<span style="color:#4be6fa">this</span>&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">+</span>&nbsp;(a&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">+</span>&nbsp;b);</div><div style="padding:0 6px; white-space:pre; line-height:130%">}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#999999">//실행&nbsp;1</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">add.apply(<span style="color:#ffd500">'정답은'</span>,&nbsp;<span style="color:#c10aff">1</span>,&nbsp;<span style="color:#c10aff">5</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#999999">//실행&nbsp;2</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">add.apply(<span style="color:#ffd500">'정답은'</span>,&nbsp;[<span style="color:#c10aff">1</span>,&nbsp;<span style="color:#c10aff">5</span>]);</div></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none;color:white"><span style="font-size:9px;word-break:normal;background-color:#4f4f4f;color:white;border-radius:10px;padding:1px">cs</span></a></td></tr></table></div>  
<a href="https://imgur.com/VGsF1BG"><img src="https://i.imgur.com/VGsF1BG.png" title="source: imgur.com" /></a>
<a href="https://imgur.com/dygnEco"><img src="https://i.imgur.com/dygnEco.png" title="source: imgur.com" /></a>  

___
# 총정리  
<div class="colorscripter-code" style="color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#272727;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #4f4f4f"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#aaa;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div><div style="line-height:130%">3</div><div style="line-height:130%">4</div><div style="line-height:130%">5</div><div style="line-height:130%">6</div><div style="line-height:130%">7</div><div style="line-height:130%">8</div><div style="line-height:130%">9</div><div style="line-height:130%">10</div><div style="line-height:130%">11</div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">function</span>&nbsp;Hello&nbsp;(<span style="color:#4be6fa">name</span>){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#4be6fa">console</span>.log(<span style="color:#ffd500">'Hello&nbsp;from'</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#4be6fa">console</span>.log(<span style="color:#4be6fa">this</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#ff3399">if</span>(<span style="color:#4be6fa">name</span>){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#4be6fa">console</span>.log(`My&nbsp;<span style="color:#4be6fa">name</span>&nbsp;is&nbsp;${<span style="color:#4be6fa">name</span>}`)</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">function</span>&nbsp;add&nbsp;(a,&nbsp;b){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#ff3399">return</span>&nbsp;<span style="color:#4be6fa">this</span>&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">+</span>&nbsp;(a&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">+</span>&nbsp;b);</div><div style="padding:0 6px; white-space:pre; line-height:130%">}</div></div><div style="text-align:right;margin-top:-13px;margin-right:5px;font-size:9px;font-style:italic"><a href="http://colorscripter.com/info#e" target="_blank" style="color:#4f4f4ftext-decoration:none">Colored by Color Scripter</a></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none;color:white"><span style="font-size:9px;word-break:normal;background-color:#4f4f4f;color:white;border-radius:10px;padding:1px">cs</span></a></td></tr></table></div>  

### 위 예제코드를 참고하자  

## Hello.bind()() === Hello.call() === Hello.apply()  
<a href="https://imgur.com/x0wuCaR"><img src="https://i.imgur.com/x0wuCaR.png" title="source: imgur.com" /></a>
<a href="https://imgur.com/0991gU0"><img src="https://i.imgur.com/0991gU0.png" title="source: imgur.com" /></a>

## Hello.bind('디스')() === Hello.call('디스') === Hello.apply('디스')  
<a href="https://imgur.com/rLQMiah"><img src="https://i.imgur.com/rLQMiah.png" title="source: imgur.com" /></a>  

## add.bind('디스', 1, 5)() === add.call('디스', 1, 5) === add.apply('디스', [1, 5])  
<a href="https://imgur.com/t312PBw"><img src="https://i.imgur.com/t312PBw.png" title="source: imgur.com" /></a>  


___
# 마무리   
누군가는 왜 더 효율적인 예제를 안내놓고,  
실용적인 예제를 안내놓냐고 할 수 있다.  
일단은 __써먹기전에 기능을 조금이라도 쉽게 알아야__ 다른 레퍼런스 문서를 보더라도  
좀 더 빨리 이해가 가기 때문이다.  
이 글을 보고 레퍼런스를 찾아보려는 이들에게 도움이 됐길 바란다.
