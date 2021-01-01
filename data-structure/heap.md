# 힙 자료구조
힙은 __우선순위 큐를 위해서__ 만들어진 특별한 자료구조다.  
이진 탐색트리와 유사한 모양을 가지고 있는데, 힙은 중복된 값을 허용하지 않는다.  
또, 힙은 완전 오름차순 형태로 정렬된게 아닌 __불완전 정렬상태__ 이다.  
우선순위 큐의 활용 사례로는,  
* 게임엔진에서 각 액터의 우선순위를 정한다.  
* 서버에서 많은 트래픽을 처리 할 때 우선처리해야할 트래픽을 정한다.  
  
다른 활용도 있는데, 이건 내가 문제를 풀거나 해봐야 할것같다.  
힙으로 우선순위큐를 구현하는 이유는 __나중에 들어온 값이라도 우선순위를 줄 수 있기 때문이다.__
___  
힙자료구조의 중점은,  
  
* __왼쪽 노드부터 삽입하고 값에 따라 부모자식 관계가 바뀌지 좌우가 바뀌지않는다.__  
* __자식노드는 부모보다 최대힙(큰거우선)일때 같거나 작으면되고,__  
* __최소힙(작은거우선)일때 크거나 같으면 된다.__  
* __완전 이진트리 상태이다.__  
  
저러한 형태의 힙을 그림으로 그려보면,  
<a href="https://imgur.com/C9mX0CM"><img src="https://i.imgur.com/C9mX0CM.png" title="source: imgur.com" /></a>  
  
0번째 인덱스는 구현 편의상 비운다.  
완전 이진트리 상태이며,  
왼쪽부터 값을 채우지만 내가 지금 그린 형태는, __최소힙(min heap)__ 이다.   

여기서 알 수있는건,  
__왼쪽자식인덱스:(자기자신의 인덱스 * 2)__ 이고  
__오른쪽자식인덱스:(자기자신의 인덱스 * 2) + 1__ 이며  
__부모인덱스:parseInt(자기자신의 인덱스 / 2)__ 이다.  
  
앞으로의 예제는 최소힙을 기준으로 하겠다.  
  
___
## 요소 삽입   
<a href="https://imgur.com/Q8ntunH"><img src="https://i.imgur.com/Q8ntunH.png" title="source: imgur.com" /></a>

이전 이미지로 작업을 하려다가 날아갔다..  

최소힙에서 새로운 요소를 삽입할 때 일어나는 과정을 살펴보자  
  
요소 -1 을 삽입해보자  
요소하나는 우선 맨끝 인덱스로 삽입이 된다.  
  
<a href="https://imgur.com/Qka2ySU"><img src="https://i.imgur.com/Qka2ySU.png" title="source: imgur.com" /></a>

  
저 상태는 분명히 최소힙 상태가 아니다.  
자식인 -1이 2보다 작기 때문이다.  
  
그래서 자신의 상단인 2와 자리를 바꾼다.  
밑에 배열도 주목해서보자.
<a href="https://imgur.com/QXX6fRN"><img src="https://i.imgur.com/QXX6fRN.png" title="source: imgur.com" /></a>  

여전히 -1은 자신의 상단보다작다.  
그래서 1과 자리를 바꾼다.  

<a href="https://imgur.com/OHzuxtv"><img src="https://i.imgur.com/OHzuxtv.png" title="source: imgur.com" /></a>  

요롷게 위계질서가 잡힐때까지 정리가되면  
삽입은 끝나게된다.  
  
___
## 요소삭제  
힙에서 삭제는 흔히들 아는 그래프에서 특정 노드를 찾아서,  
그 노드를 삭제하고 나오는게 아니라  
최소힙에서는 __요소중 최소값에해당__ 하는 요소를  
최대힙에서는 __요소중 최대값에해당__ 하는 요소를   
삭제하는 것이다.  
1번째 인덱스를 삭제하는것인데, 디큐와 똑같아보이지만, 다르다.  
디큐는 맨 앞에있는 요소를 그냥 삭제하면 그만이지만,  
우선순위가있는 힙에서 디큐는 삭제를 한 후 순서까지 다시 맞춰줘야 한다.  
  
<a href="https://imgur.com/WFYPEhF"><img src="https://i.imgur.com/WFYPEhF.png" title="source: imgur.com" /></a>  
  
위 -1을 넣은 힙에서 맨 앞 요소를 삭제해보겠다.  
<a href="https://imgur.com/XMWGjlw"><img src="https://i.imgur.com/XMWGjlw.png" title="source: imgur.com" /></a>
  
일단은 이런 혼돈이 초래하고 만다.  
그렇다고 무작정 배열을 한칸씩 앞땡기면  
모습이 어떻게될지 상상은 각자몫이다.  
  
우선은 맨 마지막 자식인 2를 땜빵시켜준다.  
<a href="https://imgur.com/F8vc2SZ"><img src="https://i.imgur.com/F8vc2SZ.png" title="source: imgur.com" /></a>  

자식들과 자기자신을 비교해서,  
자신보다 더 작은 자식이 있으면 자리를 바꿔준다.  
  
<a href="https://imgur.com/20Yq7JJ"><img src="https://i.imgur.com/20Yq7JJ.png" title="source: imgur.com" /></a>   

___  
## 최소힙 자바스크립트 코드  

<div class="colorscripter-code" style="color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#272727;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #4f4f4f"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#aaa;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div><div style="line-height:130%">3</div><div style="line-height:130%">4</div><div style="line-height:130%">5</div><div style="line-height:130%">6</div><div style="line-height:130%">7</div><div style="line-height:130%">8</div><div style="line-height:130%">9</div><div style="line-height:130%">10</div><div style="line-height:130%">11</div><div style="line-height:130%">12</div><div style="line-height:130%">13</div><div style="line-height:130%">14</div><div style="line-height:130%">15</div><div style="line-height:130%">16</div><div style="line-height:130%">17</div><div style="line-height:130%">18</div><div style="line-height:130%">19</div><div style="line-height:130%">20</div><div style="line-height:130%">21</div><div style="line-height:130%">22</div><div style="line-height:130%">23</div><div style="line-height:130%">24</div><div style="line-height:130%">25</div><div style="line-height:130%">26</div><div style="line-height:130%">27</div><div style="line-height:130%">28</div><div style="line-height:130%">29</div><div style="line-height:130%">30</div><div style="line-height:130%">31</div><div style="line-height:130%">32</div><div style="line-height:130%">33</div><div style="line-height:130%">34</div><div style="line-height:130%">35</div><div style="line-height:130%">36</div><div style="line-height:130%">37</div><div style="line-height:130%">38</div><div style="line-height:130%">39</div><div style="line-height:130%">40</div><div style="line-height:130%">41</div><div style="line-height:130%">42</div><div style="line-height:130%">43</div><div style="line-height:130%">44</div><div style="line-height:130%">45</div><div style="line-height:130%">46</div><div style="line-height:130%">47</div><div style="line-height:130%">48</div><div style="line-height:130%">49</div><div style="line-height:130%">50</div><div style="line-height:130%">51</div><div style="line-height:130%">52</div><div style="line-height:130%">53</div><div style="line-height:130%">54</div><div style="line-height:130%">55</div><div style="line-height:130%">56</div><div style="line-height:130%">57</div><div style="line-height:130%">58</div><div style="line-height:130%">59</div><div style="line-height:130%">60</div><div style="line-height:130%">61</div><div style="line-height:130%">62</div><div style="line-height:130%">63</div><div style="line-height:130%">64</div><div style="line-height:130%">65</div><div style="line-height:130%">66</div><div style="line-height:130%">67</div><div style="line-height:130%">68</div><div style="line-height:130%">69</div><div style="line-height:130%">70</div><div style="line-height:130%">71</div><div style="line-height:130%">72</div><div style="line-height:130%">73</div><div style="line-height:130%">74</div><div style="line-height:130%">75</div><div style="line-height:130%">76</div><div style="line-height:130%">77</div><div style="line-height:130%">78</div><div style="line-height:130%">79</div><div style="line-height:130%">80</div><div style="line-height:130%">81</div><div style="line-height:130%">82</div><div style="line-height:130%">83</div><div style="line-height:130%">84</div><div style="line-height:130%">85</div><div style="line-height:130%">86</div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#4be6fa">class</span>&nbsp;minHeap&nbsp;{</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#ff3399">constructor</span>&nbsp;(){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//&nbsp;요소들을&nbsp;나타낸다</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">this</span>.<span style="color:#ff3399">elements</span>&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;[,];</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#999999">//요소삽입&nbsp;메소드</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;insert(el)&nbsp;{</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//우선&nbsp;맨&nbsp;마지막&nbsp;요소에&nbsp;추가할&nbsp;엘리먼트를&nbsp;추가한다.</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//swap함수&nbsp;선언(추가한&nbsp;값의&nbsp;인덱스)</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//idx가&nbsp;0이면&nbsp;함수종료</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//요소와&nbsp;부모인덱스의&nbsp;자리를&nbsp;바꾼다.&nbsp;&nbsp;</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//idx&nbsp;=&nbsp;~~(idx&nbsp;/&nbsp;2)</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//자신의&nbsp;부모인덱스값이&nbsp;자신의값보다&nbsp;크거나&nbsp;같을&nbsp;때&nbsp;스왑</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#4be6fa">const</span>&nbsp;{<span style="color:#ff3399">elements</span>}&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#ff3399">this</span>;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">elements</span>.push(el);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#4be6fa">const</span>&nbsp;index&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#ff3399">elements</span>.<span style="color:#0086b3">length</span>&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">-</span>&nbsp;<span style="color:#c10aff">1</span>;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//바꾸는&nbsp;함수</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">function</span>&nbsp;swap(idx){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">if</span>(idx&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span><span style="color:#aaffaa"></span><span style="color:#ff3399">=</span><span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#c10aff">0</span>)<span style="color:#4be6fa">return</span>;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[<span style="color:#ff3399">elements</span>[idx],&nbsp;<span style="color:#ff3399">elements</span>[~~(idx&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">/</span>&nbsp;<span style="color:#c10aff">2</span>)]]&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;[<span style="color:#ff3399">elements</span>[~~(idx&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">/</span>&nbsp;<span style="color:#c10aff">2</span>)],&nbsp;<span style="color:#ff3399">elements</span>[idx]];</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;idx&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;~~(idx&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">/</span>&nbsp;<span style="color:#c10aff">2</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">if</span>(<span style="color:#ff3399">elements</span>[idx]&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">&lt;</span><span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#ff3399">elements</span>[~~(idx&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">/</span>&nbsp;<span style="color:#c10aff">2</span>)])swap(idx);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">if</span>(<span style="color:#ff3399">elements</span>[index]&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">&lt;</span><span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#ff3399">elements</span>[~~(index&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">/</span>&nbsp;<span style="color:#c10aff">2</span>)])swap(index);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#999999">//삭제&nbsp;메소드</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#4be6fa">delete</span>()&nbsp;{</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//우선&nbsp;맨앞요소와&nbsp;맨뒷자리애랑&nbsp;바꾼다.</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//맨뒤로간&nbsp;맨&nbsp;앞요소를&nbsp;삭제한다.</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//swap함수&nbsp;선언&nbsp;(바꿀인덱스,&nbsp;바꿔질인덱스)</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//바꿀인덱스와&nbsp;바꿔질인덱스를&nbsp;교체한다.</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//해당인덱스가&nbsp;자식을&nbsp;가지고있을때</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//왼쪽자식과&nbsp;비교해서&nbsp;해당인덱스값이&nbsp;더&nbsp;크면</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//자리교체</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//오른쪽자식과&nbsp;비교해서&nbsp;해당인덱스값이&nbsp;더&nbsp;크면</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//자리교체</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#4be6fa">const</span>&nbsp;{<span style="color:#ff3399">elements</span>}&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#ff3399">this</span>;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#4be6fa">const</span>&nbsp;backmost&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#ff3399">elements</span>.<span style="color:#0086b3">length</span>&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">-</span>&nbsp;<span style="color:#c10aff">1</span>;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;[<span style="color:#ff3399">elements</span>[<span style="color:#c10aff">1</span>],&nbsp;<span style="color:#ff3399">elements</span>[backmost]]&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;[<span style="color:#ff3399">elements</span>[backmost],&nbsp;<span style="color:#ff3399">elements</span>[<span style="color:#c10aff">1</span>]];</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">elements</span>.pop();</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">function</span>&nbsp;swap&nbsp;(change,&nbsp;changed){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[<span style="color:#ff3399">elements</span>[change],&nbsp;<span style="color:#ff3399">elements</span>[changed]]&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[<span style="color:#ff3399">elements</span>[changed],&nbsp;<span style="color:#ff3399">elements</span>[change]];</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;change&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;changed;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#4be6fa">const</span>&nbsp;leftChildIdx&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;change&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">*</span>&nbsp;<span style="color:#c10aff">2</span>;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#4be6fa">const</span>&nbsp;rightChildIdx&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;change&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">*</span>&nbsp;<span style="color:#c10aff">2</span>&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">+</span>&nbsp;<span style="color:#c10aff">1</span>;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">if</span>(<span style="color:#ff3399">elements</span>[leftChildIdx]){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">if</span>(<span style="color:#ff3399">elements</span>[leftChildIdx]&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">&lt;</span>&nbsp;<span style="color:#ff3399">elements</span>[change]){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;swap(change,&nbsp;leftChildIdx);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">if</span>(<span style="color:#ff3399">elements</span>[rightChildIdx]&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">&lt;</span>&nbsp;<span style="color:#ff3399">elements</span>[change]){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;swap(change,&nbsp;rightChildIdx);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">if</span>(<span style="color:#ff3399">elements</span>[<span style="color:#c10aff">1</span>]&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">&gt;</span>&nbsp;<span style="color:#ff3399">elements</span>[<span style="color:#c10aff">2</span>])&nbsp;swap(<span style="color:#c10aff">1</span>,&nbsp;<span style="color:#c10aff">2</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">if</span>(<span style="color:#ff3399">elements</span>[<span style="color:#c10aff">1</span>]&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">&gt;</span>&nbsp;<span style="color:#ff3399">elements</span>[<span style="color:#c10aff">3</span>])&nbsp;swap(<span style="color:#c10aff">1</span>,&nbsp;<span style="color:#c10aff">3</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">}</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#999999">/*&nbsp;test&nbsp;*/</span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#4be6fa">const</span>&nbsp;heap&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#4be6fa">new</span>&nbsp;minHeap();</div><div style="padding:0 6px; white-space:pre; line-height:130%">heap.insert(<span style="color:#c10aff">1</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">heap.insert(<span style="color:#c10aff">3</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">heap.insert(<span style="color:#c10aff">2</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">heap.insert(<span style="color:#c10aff">6</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">heap.insert(<span style="color:#c10aff">9</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">console</span>.log(heap.<span style="color:#ff3399">elements</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">heap.insert(<span style="color:#aaffaa"></span><span style="color:#ff3399">-</span><span style="color:#c10aff">1</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">console</span>.log(heap.<span style="color:#ff3399">elements</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">heap.<span style="color:#4be6fa">delete</span>();</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">console</span>.log(heap.<span style="color:#ff3399">elements</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">heap.<span style="color:#4be6fa">delete</span>();</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">console</span>.log(heap.<span style="color:#ff3399">elements</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">heap.<span style="color:#4be6fa">delete</span>();</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">console</span>.log(heap.<span style="color:#ff3399">elements</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">heap.insert(<span style="color:#c10aff">1</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">console</span>.log(heap.<span style="color:#ff3399">elements</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">heap.insert(<span style="color:#c10aff">11</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">heap.insert(<span style="color:#c10aff">4</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">heap.insert(<span style="color:#c10aff">2</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">console</span>.log(heap.<span style="color:#ff3399">elements</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">heap.<span style="color:#4be6fa">delete</span>();</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">console</span>.log(heap.<span style="color:#ff3399">elements</span>);</div></div><div style="text-align:right;margin-top:-13px;margin-right:5px;font-size:9px;font-style:italic"><a href="http://colorscripter.com/info#e" target="_blank" style="color:#4f4f4ftext-decoration:none">Colored by Color Scripter</a></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none;color:white"><span style="font-size:9px;word-break:normal;background-color:#4f4f4f;color:white;border-radius:10px;padding:1px">cs</span></a></td></tr></table></div>

### 테스트 결과  
<a href="https://imgur.com/tO6Z1rL"><img src="https://i.imgur.com/tO6Z1rL.png" title="source: imgur.com" /></a>

___