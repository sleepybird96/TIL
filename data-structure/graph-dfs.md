# 그래프와 탐색
자료구조를 학습하면서 트리를 탐색할 때에는 비교적으로,  
계층적 구조를 가지기 때문에(부모가 있음) 재귀를 통해 탐색이 쉬웠다.  
그러나, 그래프는 서로의 관계를 나타내는 간선만 있을 뿐더러, __계층구조 또한 존재하지 않는다.__  
그러나 의외로 __방문한 곳을 표시__ 하는것만 빼면,  __탐색하는 로직은 트리와 크게 다르지않다.__  
___
# 우선 예쁘고 실용적인 그래프를 만들어 보자.  
__예쁜그래프란?__  
나는 그래프의 제일 적절한 활용예를 sns친구목록이라 생각한다.  
숫자놀이로 구현하는것은 __예쁜그래프가 아니다!__  
부트캠프에서 좋은 뼈대를 내줬지만, __사람이름으로 관계도를 형성하는 그래프를 그리고 싶다.__
  
## 내가 만들 그래프에는 constructor는 필요하지않다.  
우선 constructor는 해당 class의 기본값을 설정한다.  
하지만 기본값이 필요없다.  
우선은 __기초적인 CRUD기능을 만들어보자__

## C: create  그래프에 사람을 추가해보자  
기본값은 없지만 이미 임의의 __객체가 만들어질 준비가 된 상태다.__  
그래프 안에 사람을 추가해줄 메소드를 만들어보자.  
동명이인일 경우는 __일단 생각하지말자.__


### 코드로 나타내보자!
<div class="colorscripter-code" style="color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#272727;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #4f4f4f"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#aaa;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div><div style="line-height:130%">3</div><div style="line-height:130%">4</div><div style="line-height:130%">5</div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">class</span>&nbsp;Graph{</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;addPeople(<span style="color:#4be6fa">name</span>){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#4be6fa">this</span>[<span style="color:#4be6fa">name</span>]&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;[];</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">}</div></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none;color:white"><span style="font-size:9px;word-break:normal;background-color:#4f4f4f;color:white;border-radius:10px;padding:1px">cs</span></a></td></tr></table></div>  

간단하지 않은가?  
키값인 __이름에 들어가는 밸류인 배열에 edge(관계)를 추가할거다__  
바로 만든 메소드를 활용해 사람을 추가해보자.  
<a href="https://imgur.com/PjGJNmr"><img src="https://i.imgur.com/PjGJNmr.png" title="source: imgur.com" /></a>  

### 그림으로 나타낸다면?
<a href="https://imgur.com/7fOSw0a"><img src="https://i.imgur.com/7fOSw0a.png" title="source: imgur.com" /></a>  

people이라는 객체에 __메소드를 통해 추가된 인원이 총 5명이다.__  
나중에 탐색 이해를 돕기 위해 두사람 더 추가하자.  
<a href="https://imgur.com/UIB2qR6"><img src="https://i.imgur.com/UIB2qR6.png" title="source: imgur.com" /></a>  

## R: read 서로의 관계를 확인하고, U: update 관계를 추가하자.  
makeFriend라는 메소드를 통해 관계를 추가하자.  
각 __이름(키)에 해당하는 배열에 친구가 될 이름을 푸쉬한다.__   
그리고 __둘이 친구면 true 친구가아니면 false를 내뱉자.__ 

### 코드로 나타내보자!
<div class="colorscripter-code" style="color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#272727;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #4f4f4f"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#aaa;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div><div style="line-height:130%">3</div><div style="line-height:130%">4</div><div style="line-height:130%">5</div><div style="line-height:130%">6</div><div style="line-height:130%">7</div><div style="line-height:130%">8</div><div style="line-height:130%">9</div><div style="line-height:130%">10</div><div style="line-height:130%">11</div><div style="line-height:130%">12</div><div style="line-height:130%">13</div><div style="line-height:130%">14</div><div style="line-height:130%">15</div><div style="line-height:130%">16</div><div style="line-height:130%">17</div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">class</span>&nbsp;Graph{</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;addPeople(<span style="color:#4be6fa">name</span>){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#4be6fa">this</span>[<span style="color:#4be6fa">name</span>]&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;[];</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;makeFriend(name1,&nbsp;name2){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#4be6fa">this</span>[name1].push(name2);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#4be6fa">this</span>[name2].push(name1);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;isFriend(name1,&nbsp;name2){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">if</span>(<span style="color:#4be6fa">this</span>[name1].<span style="color:#4be6fa">indexOf</span>(name2)&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">!</span><span style="color:#aaffaa"></span><span style="color:#ff3399">=</span><span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">-</span><span style="color:#c10aff">1</span>){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">return</span>&nbsp;<span style="color:#ff3399">true</span>;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">return</span>&nbsp;<span style="color:#c10aff">false</span>;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">}</div></div><div style="text-align:right;margin-top:-13px;margin-right:5px;font-size:9px;font-style:italic"><a href="http://colorscripter.com/info#e" target="_blank" style="color:#4f4f4ftext-decoration:none">Colored by Color Scripter</a></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none;color:white"><span style="font-size:9px;word-break:normal;background-color:#4f4f4f;color:white;border-radius:10px;padding:1px">cs</span></a></td></tr></table></div>

역시나 메소드를 통해 추가해보자.  
<a href="https://imgur.com/9qoun3N"><img src="https://i.imgur.com/9qoun3N.png" title="source: imgur.com" /></a>  

### 그림으로 나타내면?
<a href="https://imgur.com/IMSpoqX"><img src="https://i.imgur.com/IMSpoqX.png" title="source: imgur.com" /></a>  
나만 인싸가 된 모습이다.  
탐색을 용이하게 하기위해 관계를 더 복잡하게 형성하자.  
<a href="https://imgur.com/vp2JrwE"><img src="https://i.imgur.com/vp2JrwE.png" title="source: imgur.com" /></a>

<a href="https://imgur.com/V67faYI"><img src="https://i.imgur.com/V67faYI.png" title="source: imgur.com" /></a>  

__isFriend메소드로 친구인지 확인하자__  
<a href="https://imgur.com/sq0cNzQ"><img src="https://i.imgur.com/sq0cNzQ.png" title="source: imgur.com" /></a>  


## D: delete 아예탈퇴하는 메소드와, 친구관계를 끊는 메소드를 만들자.  
아예 people이라는 객체를 나가버리는 leave메소드와,  
서로의 친구관계만 끊어버리는 burnBridges를 만들어보자.  

### leave라는 메소드는 전체 친구목록에도 사라져야한다.  
<a href="https://imgur.com/fufx6ms"><img src="https://i.imgur.com/fufx6ms.png" title="source: imgur.com" /></a>  

### burnBridges 메소드는 서로의 관계만 끊어야 한다.  
<a href="https://imgur.com/v0QysKg"><img src="https://i.imgur.com/v0QysKg.png" title="source: imgur.com" /></a>  
  
___  

우선 내가 원하던 사람과 사람사이의 사이를 나타내는 그래프를 완성했다.  
기본적인 CRUD기능을 만들었다면 이젠, __Read를 극대화한 탐색기능을 구현해보자__  
그래프의 탐색에는 __깊이우선탐색(DFS)__ 그리고 __너비우선탐색(BFS)__ 가 있다

## 깊이를 우선으로 탐색한다는게 뭐에요?  
다른곳 보면 말도참 어렵게도 했는데,  
초등학생도 알아먹을만큼 쉽게 설명해본다.  
  
### 1. __시작점 부터 방문기록을 남긴다.__ 방문을 안한곳 중 갈 수 있는데 까지 한길로 끝까지 일단 간다. 가는곳 마다 __방문기록 남기는건 필수 ><__ 
### 2. 더이상 갈 곳이 없으면 왔던길로 한번 돌아오자 
### 3. 돌아왔는데 갈 곳이 있으면 또 그길로(방문안한곳만) 끝까지 간다.

# 재밌는 DFS 시작해보자!  
우선 그림으로 먼저 그려보자.  
아까 쓴 그림 그대로 쓸거다   

<a href="https://imgur.com/vp2JrwE"><img src="https://i.imgur.com/vp2JrwE.png" title="source: imgur.com" /></a>  

## 1. 시작점 부터 방문을 안한곳 중 갈 수 있는데 까지 __한길로__ 끝까지 일단 간다.  
일단 박지상 부터 시작해서 욜씨미 가보자><  
__그림에서 방문기록은 체크로 표시한다__  

### __박지상에 방문함. 갈곳 네가지 있는데 첫번째 선택지인 박준석갈거임__  
<a href="https://imgur.com/M9ZKxMz"><img src="https://i.imgur.com/M9ZKxMz.png" title="source: imgur.com" /></a>  

### __박준석에 방문함. 박지상엔 방문했고 김제현 밖에 갈곳없음__  
<a href="https://imgur.com/S6yKcnZ"><img src="https://i.imgur.com/S6yKcnZ.png" title="source: imgur.com" /></a>  

### __김제현에 방문함. 박준석 방문했고, 갈곳 두가지있는데 박준석 방문했으니 그다음 순서인 이상권갈거임__  
<a href="https://imgur.com/C27Ca1v"><img src="https://i.imgur.com/C27Ca1v.png" title="source: imgur.com" /></a>  

<a href="https://imgur.com/s4pzJhx"><img src="https://i.imgur.com/s4pzJhx.png" title="source: imgur.com" /></a>  

### __이상권에 방문함. 왔는데 갈데없어서 돌아갈거임.__  
<a href="https://imgur.com/j4PVLGw"><img src="https://i.imgur.com/j4PVLGw.png" title="source: imgur.com" /></a>  

<a href="https://imgur.com/9toTts5"><img src="https://i.imgur.com/9toTts5.png" title="source: imgur.com" /></a>  

### __김제현으로 돌아옴. 왔는데 방문안한 곳이 김코딩뿐임.__  
<a href="https://imgur.com/V3N95JC"><img src="https://i.imgur.com/V3N95JC.png" title="source: imgur.com" /></a>  

<a href="https://imgur.com/VFeJ7gb"><img src="https://i.imgur.com/VFeJ7gb.png" title="source: imgur.com" /></a>

### __김코딩에 방문함. 갈곳은 김해커뿐임__  

<a href="https://imgur.com/EwQT4xg"><img src="https://i.imgur.com/EwQT4xg.png" title="source: imgur.com" /></a>

<a href="https://imgur.com/qWGmOQd"><img src="https://i.imgur.com/qWGmOQd.png" title="source: imgur.com" /></a>   

### __김해커에 방문함. 더이상 갈곳이 없음__  
<a href="https://imgur.com/DQ3uKju"><img src="https://i.imgur.com/DQ3uKju.png" title="source: imgur.com" /></a>  

### __김코딩으로 돌아옴. 갈곳없음__
### __김제현으로 돌아옴. 갈곳없음__
### __박준석으로 돌아옴. 갈곳없음__  
  
### __박지상으로 돌아옴. 갈곳 김용재 딱하나 있음__  
### __김용재로 돌아옴. 갈곳 아무데도 없음__  
<a href="https://imgur.com/cHQTzJj"><img src="https://i.imgur.com/cHQTzJj.png" title="source: imgur.com" /></a>  

### 함수종료  
  
위와 같은 방식을 재귀로 쉽게 구현할 수 있다.  
재귀함수의 베이스값이 바로 돌아오는 역할을 한다!  
  
우선 각 노드마다 방문했는지 여부를 알 수 있는 장치를 만들자.
  
각각 회원들의 밸류값을 2차원배열로 바꾸고  
__0번째 인덱스에는 친구목록__  
__1번째 인덱스에는 방문여부__ 를 넣어준다.
<a href="https://imgur.com/ILOTBMH"><img src="https://i.imgur.com/ILOTBMH.png" title="source: imgur.com" /></a>
  
## DFS까지 구현한 코드  
<div class="colorscripter-code" style="color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#272727;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #4f4f4f"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#aaa;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div><div style="line-height:130%">3</div><div style="line-height:130%">4</div><div style="line-height:130%">5</div><div style="line-height:130%">6</div><div style="line-height:130%">7</div><div style="line-height:130%">8</div><div style="line-height:130%">9</div><div style="line-height:130%">10</div><div style="line-height:130%">11</div><div style="line-height:130%">12</div><div style="line-height:130%">13</div><div style="line-height:130%">14</div><div style="line-height:130%">15</div><div style="line-height:130%">16</div><div style="line-height:130%">17</div><div style="line-height:130%">18</div><div style="line-height:130%">19</div><div style="line-height:130%">20</div><div style="line-height:130%">21</div><div style="line-height:130%">22</div><div style="line-height:130%">23</div><div style="line-height:130%">24</div><div style="line-height:130%">25</div><div style="line-height:130%">26</div><div style="line-height:130%">27</div><div style="line-height:130%">28</div><div style="line-height:130%">29</div><div style="line-height:130%">30</div><div style="line-height:130%">31</div><div style="line-height:130%">32</div><div style="line-height:130%">33</div><div style="line-height:130%">34</div><div style="line-height:130%">35</div><div style="line-height:130%">36</div><div style="line-height:130%">37</div><div style="line-height:130%">38</div><div style="line-height:130%">39</div><div style="line-height:130%">40</div><div style="line-height:130%">41</div><div style="line-height:130%">42</div><div style="line-height:130%">43</div><div style="line-height:130%">44</div><div style="line-height:130%">45</div><div style="line-height:130%">46</div><div style="line-height:130%">47</div><div style="line-height:130%">48</div><div style="line-height:130%">49</div><div style="line-height:130%">50</div><div style="line-height:130%">51</div><div style="line-height:130%">52</div><div style="line-height:130%">53</div><div style="line-height:130%">54</div><div style="line-height:130%">55</div><div style="line-height:130%">56</div><div style="line-height:130%">57</div><div style="line-height:130%">58</div><div style="line-height:130%">59</div><div style="line-height:130%">60</div><div style="line-height:130%">61</div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">class</span>&nbsp;Graph{</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#999999">//SNS에서의&nbsp;회원가입이라고&nbsp;생각하자.</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;addPeople(<span style="color:#4be6fa">name</span>){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#4be6fa">this</span>[<span style="color:#4be6fa">name</span>]&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;[[],<span style="color:#c10aff">false</span>];</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#999999">//SNS에서의&nbsp;친구추가라고&nbsp;생각하자.</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;makeFriend(name1,&nbsp;name2){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#4be6fa">this</span>[name1][<span style="color:#c10aff">0</span>].push(name2);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#4be6fa">this</span>[name2][<span style="color:#c10aff">0</span>].push(name1);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#999999">//두&nbsp;인자가&nbsp;친구인지&nbsp;확인한다.</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;isFriend(name1,&nbsp;name2){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">if</span>(<span style="color:#4be6fa">this</span>[name1][<span style="color:#c10aff">0</span>].<span style="color:#4be6fa">indexOf</span>(name2)&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">!</span><span style="color:#aaffaa"></span><span style="color:#ff3399">=</span><span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">-</span><span style="color:#c10aff">1</span>){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">return</span>&nbsp;<span style="color:#ff3399">true</span>;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">return</span>&nbsp;<span style="color:#c10aff">false</span>;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#999999">//SNS에서의&nbsp;회원탈퇴라고&nbsp;생각하자.</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;leave(<span style="color:#4be6fa">name</span>){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">delete</span>&nbsp;<span style="color:#4be6fa">this</span>[<span style="color:#4be6fa">name</span>];</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">for</span>(<span style="color:#ff3399">let</span>&nbsp;key&nbsp;<span style="color:#ff3399">in</span>&nbsp;<span style="color:#4be6fa">this</span>){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">if</span>&nbsp;(<span style="color:#4be6fa">this</span>[key][<span style="color:#c10aff">0</span>].<span style="color:#4be6fa">indexOf</span>(<span style="color:#4be6fa">name</span>)&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">!</span><span style="color:#aaffaa"></span><span style="color:#ff3399">=</span><span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">-</span><span style="color:#c10aff">1</span>){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#4be6fa">this</span>[key][<span style="color:#c10aff">0</span>].splice(<span style="color:#4be6fa">this</span>[key][<span style="color:#c10aff">0</span>].<span style="color:#4be6fa">indexOf</span>(<span style="color:#4be6fa">name</span>),&nbsp;<span style="color:#c10aff">1</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#999999">//SNS에서&nbsp;친구삭제라고&nbsp;생각하자.&nbsp;차단이라&nbsp;생각해도&nbsp;좋다.</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;burnBridge(name1,&nbsp;name2){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">let</span>&nbsp;idx1&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#4be6fa">this</span>[name1][<span style="color:#c10aff">0</span>].<span style="color:#4be6fa">indexOf</span>(name2);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">let</span>&nbsp;idx2&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#4be6fa">this</span>[name2][<span style="color:#c10aff">0</span>].<span style="color:#4be6fa">indexOf</span>(name1);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#4be6fa">this</span>[name1][<span style="color:#c10aff">0</span>].splice(idx1,&nbsp;<span style="color:#c10aff">1</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#4be6fa">this</span>[name2][<span style="color:#c10aff">0</span>].splice(idx2,&nbsp;<span style="color:#c10aff">1</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#999999">//깊이우선탐색을&nbsp;한다.&nbsp;start값에는&nbsp;어느&nbsp;노드가&nbsp;들어가도&nbsp;무방하다.</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;DFS(start,&nbsp;callback){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//먼저&nbsp;방문기록을&nbsp;남긴다.</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#4be6fa">this</span>[start][<span style="color:#c10aff">1</span>]&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#ff3399">true</span>;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//&nbsp;현재&nbsp;노드에&nbsp;할려는&nbsp;행위를&nbsp;한다&nbsp;</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;callback(start);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//방문을&nbsp;안한곳&nbsp;중&nbsp;갈&nbsp;수&nbsp;있는데&nbsp;까지&nbsp;간다.</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//더이상&nbsp;갈&nbsp;곳이&nbsp;없으면&nbsp;왔던길로&nbsp;한번&nbsp;돌아오자(재귀했던&nbsp;함수가끝남)</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//돌아왔는데&nbsp;갈곳이&nbsp;있다면&nbsp;가자.</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">for</span>(<span style="color:#ff3399">let</span>&nbsp;friend&nbsp;of&nbsp;<span style="color:#4be6fa">this</span>[start][<span style="color:#c10aff">0</span>]){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">if</span>(<span style="color:#aaffaa"></span><span style="color:#ff3399">!</span><span style="color:#4be6fa">this</span>[friend][<span style="color:#c10aff">1</span>])<span style="color:#4be6fa">this</span>.DFS(friend,&nbsp;callback);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//갈곳이&nbsp;없으면&nbsp;함수가&nbsp;종료된다.</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//이&nbsp;모든게&nbsp;재귀로&nbsp;가능!</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#999999">//방문기록을&nbsp;초기화한다.</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;resetHistory(){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">for</span>(<span style="color:#ff3399">let</span>&nbsp;<span style="color:#4be6fa">history</span>&nbsp;<span style="color:#ff3399">in</span>&nbsp;<span style="color:#4be6fa">this</span>){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#4be6fa">this</span>[<span style="color:#4be6fa">history</span>][<span style="color:#c10aff">1</span>]&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#c10aff">false</span>;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">}</div></div><div style="text-align:right;margin-top:-13px;margin-right:5px;font-size:9px;font-style:italic"><a href="http://colorscripter.com/info#e" target="_blank" style="color:#4f4f4ftext-decoration:none">Colored by Color Scripter</a></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none;color:white"><span style="font-size:9px;word-break:normal;background-color:#4f4f4f;color:white;border-radius:10px;padding:1px">cs</span></a></td></tr></table></div>

## 잘 작동하는지 확인해 보자.  
<div class="colorscripter-code" style="color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#272727;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #4f4f4f"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#aaa;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div><div style="line-height:130%">3</div><div style="line-height:130%">4</div><div style="line-height:130%">5</div><div style="line-height:130%">6</div><div style="line-height:130%">7</div><div style="line-height:130%">8</div><div style="line-height:130%">9</div><div style="line-height:130%">10</div><div style="line-height:130%">11</div><div style="line-height:130%">12</div><div style="line-height:130%">13</div><div style="line-height:130%">14</div><div style="line-height:130%">15</div><div style="line-height:130%">16</div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">const</span>&nbsp;people&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#ff3399">new</span>&nbsp;Graph;</div><div style="padding:0 6px; white-space:pre; line-height:130%">people.addPeople(<span style="color:#ffd500">'박지상'</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">people.addPeople(<span style="color:#ffd500">'이상권'</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">people.addPeople(<span style="color:#ffd500">'김코딩'</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">people.addPeople(<span style="color:#ffd500">'김해커'</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">people.addPeople(<span style="color:#ffd500">'김용재'</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">people.addPeople(<span style="color:#ffd500">'김제현'</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">people.addPeople(<span style="color:#ffd500">'박준석'</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">people.makeFriend(<span style="color:#ffd500">'박지상'</span>,<span style="color:#ffd500">'박준석'</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">people.makeFriend(<span style="color:#ffd500">'박지상'</span>,<span style="color:#ffd500">'이상권'</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">people.makeFriend(<span style="color:#ffd500">'박지상'</span>,<span style="color:#ffd500">'김용재'</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">people.makeFriend(<span style="color:#ffd500">'박지상'</span>,<span style="color:#ffd500">'김해커'</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">people.makeFriend(<span style="color:#ffd500">'박준석'</span>,<span style="color:#ffd500">'김제현'</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">people.makeFriend(<span style="color:#ffd500">'이상권'</span>,<span style="color:#ffd500">'김제현'</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">people.makeFriend(<span style="color:#ffd500">'김코딩'</span>,<span style="color:#ffd500">'김제현'</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">people.makeFriend(<span style="color:#ffd500">'김코딩'</span>,<span style="color:#ffd500">'김해커'</span>);</div></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none;color:white"><span style="font-size:9px;word-break:normal;background-color:#4f4f4f;color:white;border-radius:10px;padding:1px">cs</span></a></td></tr></table></div>  

우선은 아까 계속 예시를 들었던 그림과 같이 친구들을 추가해준다.  
  
SNS의 이웃이나 친구를 넘나들면서   
__광고를 남겨대는 사람__ 들을 보았는가?  
어쩌면 사람이 아닐수도 있다.  

## 광고봇을 콜백함수로 만들어보자  
<div class="colorscripter-code" style="color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#272727;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #4f4f4f"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#aaa;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">const</span>&nbsp;adBot&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;friend<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span><span style="color:#aaffaa"></span><span style="color:#ff3399">&gt;</span><span style="color:#4be6fa">console</span>.log(`${friend}의&nbsp;방명록에&nbsp;광고남김`)</div><div style="padding:0 6px; white-space:pre; line-height:130%">people.DFS(<span style="color:#ffd500">'박지상'</span>,&nbsp;adBot);</div></div><div style="text-align:right;margin-top:-13px;margin-right:5px;font-size:9px;font-style:italic"><a href="http://colorscripter.com/info#e" target="_blank" style="color:#4f4f4ftext-decoration:none">Colored by Color Scripter</a></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none;color:white"><span style="font-size:9px;word-break:normal;background-color:#4f4f4f;color:white;border-radius:10px;padding:1px">cs</span></a></td></tr></table></div>

</br>

믿기힘들겠지만 광고봇이다. 그렇다고 해줘..  
시작점을 정하고 메소드를 실행시키자.  

<a href="https://imgur.com/h0hWB4m"><img src="https://i.imgur.com/h0hWB4m.png" title="source: imgur.com" /></a>  

아까 그림의 순서대로 광고를 남긴걸 볼 수 있다.  
  
다른사람을 포인트로 해도 작동하는지 보자.  
  
우선 광고봇이 헷갈리지않게 방문기록을 초기화시켜준다.  
<a href="https://imgur.com/3nnPFnR"><img src="https://i.imgur.com/3nnPFnR.png" title="source: imgur.com" /></a>  

기록이 잘 초기화 되었다.  
김코딩을 넣고 실행시켜보자.  

<a href="https://imgur.com/jT3dnNE"><img src="https://i.imgur.com/jT3dnNE.png" title="source: imgur.com" /></a>  

훌륭하게 임무를 수행하는 광고봇이다.  
다음엔 알고리즘 카테고리에서 __너비우선탐색인 BFS__ 를 알아보자
___
위 코드는 모두 필자의 머릿속에서 작성됐습니다.  
참조해서 올리실때 __댓글만 달아주시면__ 압도적감사!