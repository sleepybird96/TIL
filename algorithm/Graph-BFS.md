# 그래프 너비 우선 탐색법
너비 우선탐색은 깊이탐색과 함께 등장하는 탐색방법이다.  
깊이우선탐색은 __갈수있는데까지 깊이__ 갔다오는걸 반복한다면,  
너비우선 탐색은 __갈수있는 길목을 한단계씩 차례대로__ 가보는거다.  
  
ex)깊이우선탐색
<a href="https://imgur.com/JLtnXeU"><img src="https://i.imgur.com/JLtnXeU.png" title="source: imgur.com" /></a>  
[깊이우선탐색설명](https://sleepybird.tistory.com/128)
  
ex)너비우선탐색  
<a href="https://imgur.com/Jojl02x"><img src="https://i.imgur.com/Jojl02x.png" title="source: imgur.com" /></a>  
  
보다시피 깊이우선탐색은 __일단 깊이 찌르는것과 달리__  
갈수있는 길목을 __한칸씩만 가고__ 다음길목으로 가서 __또 갈길을 체크한다.__  
  
갈수있는 길목을 순차적으로 살피게 해줄 도구가 필요한데,  
바로 __큐__ 자료구조를 이용하는것이다.  
  
<a href="https://imgur.com/4qGztd6"><img src="https://i.imgur.com/4qGztd6.png" title="source: imgur.com" /></a>  
  
이해를 돕기위해 숫자 순서를 섞는다.  

bfs도 순서를 나열하면 간단하다.  
### 1. 현재 위치한곳에 방문기록을 표시한다.  
### 2. 디큐한다.  
### 3. 갈 수 있는 길목중에 방문한적이 없고 큐에 없는 노드를 인큐한다.  
### 4. 큐에있는 노드들을 bfs(재귀)한다.  
  
</br>

### __start에 방문기록 표시__
<a href="https://imgur.com/aFA3MiE"><img src="https://i.imgur.com/aFA3MiE.png" title="source: imgur.com" /></a>  
  
### __디큐한다__  
현재 큐에 아무것도 없다. 

</br>
  
  
### __start에서 갈수있는 곳은 3, 5, 1 셋다 방문기록전무, 큐에도 암것도없다__  
<a href="https://imgur.com/umdjwCU"><img src="https://i.imgur.com/umdjwCU.png" title="source: imgur.com" /></a>  
그래서 큐에 3, 5, 1 이 추가된걸 볼수있다.  

</br>

### 큐를순회하면서 시작지점을 큐의 각요소로 잡고 BFS를 한다.  
  
</br>

### 3을 BFS한다 -> 현재위치한 3에 방문기록을 표시한다.  
<a href="https://imgur.com/0HdixQD"><img src="https://i.imgur.com/0HdixQD.png" title="source: imgur.com" /></a>  

</br>

### 디큐한다.  
<a href="https://imgur.com/pNzdJeN"><img src="https://i.imgur.com/pNzdJeN.png" title="source: imgur.com" /></a>  
  
### 갈수있는 길목인 4를 인큐한다.  
<a href="https://imgur.com/JFLCKou"><img src="https://i.imgur.com/JFLCKou.png" title="source: imgur.com" /></a>

### 큐를순회하면서 시작지점을 큐의 각요소로 잡고 BFS를 한다.  

</br>  

### 5를 BFS한다 -> 현재 위치한 5에 방문기록을 표시한다. 
<a href="https://imgur.com/Cfp73AZ"><img src="https://i.imgur.com/Cfp73AZ.png" title="source: imgur.com" /></a> 
</br>

### 디큐한다.  
<a href="https://imgur.com/Pfav7XI"><img src="https://i.imgur.com/Pfav7XI.png" title="source: imgur.com" /></a>  

  
### 갈수있는 길목이 있긴하지만, 큐에 이미있다.  
</br>

### 큐를순회하면서 시작지점을 큐의 각요소로 잡고 BFS를 한다.  
</br>

### 1을 BFS한다 -> 현재 위치한 1에 방문기록을 표시한다.  
<a href="https://imgur.com/kEzpnty"><img src="https://i.imgur.com/kEzpnty.png" title="source: imgur.com" /></a>

  
### 디큐한다.
<a href="https://imgur.com/9dzRN3h"><img src="https://i.imgur.com/9dzRN3h.png" title="source: imgur.com" /></a>  

### 더이상 갈 곳이없고 큐에 넣을것도 없다.  
  
  
### 큐를순회하면서 시작지점을 큐의 각요소로 잡고 BFS를 한다.  
</br>

### 4를 BFS한다 -> 현재 위치한 4에 방문기록을 표시한다.  
<a href="https://imgur.com/YuRldCK"><img src="https://i.imgur.com/YuRldCK.png" title="source: imgur.com" /></a>  

  
### 디큐한다.  
<a href="https://imgur.com/cQMRPW7"><img src="https://i.imgur.com/cQMRPW7.png" title="source: imgur.com" /></a>  

### 갈수있는 길목인 2를 인큐한다.  
<a href="https://imgur.com/oXCWKW5"><img src="https://i.imgur.com/oXCWKW5.png" title="source: imgur.com" /></a>

  
### 큐를순회하면서 시작지점을 큐의 각요소로 잡고 BFS를 한다.  
</br>

### 2를 BFS한다 -> 현재 위치한 2에 방문기록을 표시한다.  
<a href="https://imgur.com/lrrDlqY"><img src="https://i.imgur.com/lrrDlqY.png" title="source: imgur.com" /></a>


### 디큐한다.  
<a href="https://imgur.com/9JfrA8s"><img src="https://i.imgur.com/9JfrA8s.png" title="source: imgur.com" /></a>  

### 함수종료  

  
## javascript 코드로 구현해보자.  
<div class="colorscripter-code" style="color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#272727;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #4f4f4f"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#aaa;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div><div style="line-height:130%">3</div><div style="line-height:130%">4</div><div style="line-height:130%">5</div><div style="line-height:130%">6</div><div style="line-height:130%">7</div><div style="line-height:130%">8</div><div style="line-height:130%">9</div><div style="line-height:130%">10</div><div style="line-height:130%">11</div><div style="line-height:130%">12</div><div style="line-height:130%">13</div><div style="line-height:130%">14</div><div style="line-height:130%">15</div><div style="line-height:130%">16</div><div style="line-height:130%">17</div><div style="line-height:130%">18</div><div style="line-height:130%">19</div><div style="line-height:130%">20</div><div style="line-height:130%">21</div><div style="line-height:130%">22</div><div style="line-height:130%">23</div><div style="line-height:130%">24</div><div style="line-height:130%">25</div><div style="line-height:130%">26</div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">const</span>&nbsp;graph&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;{<span style="color:#999999">//2차원배열의&nbsp;1번째인덱스는&nbsp;방문여부이다.</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;start:&nbsp;[[<span style="color:#c10aff">3</span>,&nbsp;<span style="color:#c10aff">5</span>,&nbsp;<span style="color:#c10aff">1</span>],&nbsp;<span style="color:#c10aff">false</span>],</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#c10aff">3</span>:&nbsp;[[<span style="color:#c10aff">4</span>,&nbsp;<span style="color:#ffd500">'start'</span>],&nbsp;<span style="color:#c10aff">false</span>],</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#c10aff">5</span>:&nbsp;[[<span style="color:#c10aff">4</span>,&nbsp;<span style="color:#c10aff">1</span>,&nbsp;<span style="color:#ffd500">'start'</span>],&nbsp;<span style="color:#c10aff">false</span>],</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#c10aff">1</span>:&nbsp;[[<span style="color:#ffd500">'start'</span>,&nbsp;<span style="color:#c10aff">5</span>],&nbsp;<span style="color:#c10aff">false</span>],</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#c10aff">4</span>:&nbsp;[[<span style="color:#c10aff">2</span>,&nbsp;<span style="color:#c10aff">5</span>,&nbsp;<span style="color:#c10aff">3</span>],&nbsp;<span style="color:#c10aff">false</span>],</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#c10aff">2</span>:&nbsp;[[<span style="color:#c10aff">4</span>],&nbsp;<span style="color:#c10aff">false</span>]</div><div style="padding:0 6px; white-space:pre; line-height:130%">}</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">const</span>&nbsp;que&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;[];</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">function</span>&nbsp;BFS(begin){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#999999">//현재노드에&nbsp;방문기록을&nbsp;남긴다.</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;graph[begin][<span style="color:#c10aff">1</span>]&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#ff3399">true</span>;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#4be6fa">console</span>.log(`${begin}&nbsp;에&nbsp;방문함`);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#999999">//디큐한다.</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;que.shift();</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#999999">//방문한적이&nbsp;없고,&nbsp;큐에&nbsp;없는&nbsp;노드를&nbsp;인큐한다.</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#ff3399">for</span>(<span style="color:#ff3399">let</span>&nbsp;el&nbsp;of&nbsp;graph[begin][<span style="color:#c10aff">0</span>]){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">if</span>(<span style="color:#aaffaa"></span><span style="color:#ff3399">!</span>graph[el][<span style="color:#c10aff">1</span>]&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">&amp;</span><span style="color:#aaffaa"></span><span style="color:#ff3399">&amp;</span>&nbsp;que.<span style="color:#4be6fa">indexOf</span>(el)&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span><span style="color:#aaffaa"></span><span style="color:#ff3399">=</span><span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">-</span><span style="color:#c10aff">1</span>){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;que.push(el)</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#999999">//큐를&nbsp;순회하며&nbsp;각요소를&nbsp;BFS한다</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#ff3399">for</span>(<span style="color:#ff3399">let</span>&nbsp;el&nbsp;of&nbsp;que){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;BFS(el)</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">}</div></div><div style="text-align:right;margin-top:-13px;margin-right:5px;font-size:9px;font-style:italic"><a href="http://colorscripter.com/info#e" target="_blank" style="color:#4f4f4ftext-decoration:none">Colored by Color Scripter</a></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none;color:white"><span style="font-size:9px;word-break:normal;background-color:#4f4f4f;color:white;border-radius:10px;padding:1px">cs</span></a></td></tr></table></div>
</br>
  
<a href="https://imgur.com/twken31"><img src="https://i.imgur.com/twken31.png" title="source: imgur.com" /></a>

위 예제와 같은 인접리스트 배열로 그래프를 대강 만들어봤다.  
지금 중점은 탐색이니 그래프의 여러기능을 구현한 포스트는 [여기](https://sleepybird.tistory.com/128)  