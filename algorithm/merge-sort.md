# 병합정렬 알고리즘  
합병정렬은 맨해튼 프로젝트에 참여했던 폰노이만이 제안한 방법이다.  
<a href="https://imgur.com/Pcq5gZC"><img src="https://i.imgur.com/Pcq5gZC.png" title="source: imgur.com" /></a>  

시간복잡도를 최악의경우에도 O(n log n)만큼 줄이는 방법인데,  
기존 정렬알고리즘보다 확연히 줄어든다.  
또 간단하다
  
합병정렬에는 크게 두가지 역할을 수행해야된다.  
  
1. 좌 우를 기준으로 재귀적으로 나누기  
2. 좌 우에다가 정렬된 두 배열을 합치는 함수 적용하기
  
나는 이 원리가 이해됐지만 처음 배웠을 땐 도저히 __배열의 길이가 짝수일 때는 어떻게 해?__ 라는 의문을 풀어낼 수 없었다.  
그래서 썼던 방법이 있는데 __그림이나 종이로 숫자카드를 그리고 정렬__ 해보기였다. 

___

## 1. 좌 우를 기준으로 재귀적으로 나누기
  
아래와 같은 배열이 있다.  

  
<a href="https://imgur.com/7KVHy52"><img src="https://i.imgur.com/7KVHy52.png" title="source: imgur.com" /></a>

</br>  

이걸 딱 반틈만큼 잘라줘야 하는데,  
배열의길이가 보다시피 홀수이다.  
나누기 2를하면 4.5이고 뒤에 소수점을 땐 것만큼 잘라주자.  
  
<a href="https://imgur.com/XmnoMp7"><img src="https://i.imgur.com/XmnoMp7.png" title="source: imgur.com" /></a>  
이렇게 지속적으로 나눈다면,  
원소가 하나밖에 없어서 __left Right를 안가지는 경우__ 가 있을건데,  
그럴때는 그냥 그 값 자체를 놔두자.  
<a href="https://imgur.com/Zx2PXw4"><img src="https://i.imgur.com/Zx2PXw4.png" title="source: imgur.com" /></a>  
재귀적으로 좌우 나눴다면 위와 같은 형태가 된다.  
___  

## 2. 오름차순으로 정렬된 두 배열을 비교하고 합치는 함수
  
__오름차순으로 정렬된__ 두 배열을 합치는것이다.  
결코 아무배열이나 합쳐지는것이 아님을 명심하자!  
  
<a href="https://imgur.com/W74T51f"><img src="https://i.imgur.com/W74T51f.png" title="source: imgur.com" /></a>  
  
위와 같이 오름차순으로 정렬된 두 배열을  
__크기를 비교해가며__  결과배열에 푸쉬해줄거다.  
  
__둘다__ 배열의 길이가 __0이 아닐동안__  
  
각 배열의 0번째 인덱스를 비교한다.  
<a href="https://imgur.com/vuuc1PL"><img src="https://i.imgur.com/vuuc1PL.png" title="source: imgur.com" /></a>  

더 작은 값을 __꺼내서 결과에 푸쉬한다__  
<a href="https://imgur.com/sjSLdhr"><img src="https://i.imgur.com/sjSLdhr.png" title="source: imgur.com" /></a>  
  
각 배열의 0번째 인덱스를 비교한다.  
<a href="https://imgur.com/QjhiN3B"><img src="https://i.imgur.com/QjhiN3B.png" title="source: imgur.com" /></a>  

더 작은 값을 __꺼내서 결과에 푸쉬한다__  
<a href="https://imgur.com/Lyvon4f"><img src="https://i.imgur.com/Lyvon4f.png" title="source: imgur.com" /></a>  

한쪽배열의 길이가 0이 됐으므로 벗어난다.  
  
길이가 __0이 아닌 배열의 길이가 0이될때동안__  

배열의 __맨 앞부분을 꺼내서 결과배열에 푸쉬한다__  
<a href="https://imgur.com/F44lzAf"><img src="https://i.imgur.com/F44lzAf.png" title="source: imgur.com" /></a>  

___  
두 기능을 알아보았으니 수도코드를 어떻게 짤지 그림을 그려가며 생각을 해보자  
  
### 1. 배열을 좌 우로 나눈다.  
<a href="https://imgur.com/XmnoMp7"><img src="https://i.imgur.com/XmnoMp7.png" title="source: imgur.com" /></a>  

좌 우를 바로 비교하고 병합하는 함수를 적용하면 어떻게 될까?  
오름차순으로 정렬되지 않았기에,  
순서가 마음대로 섞일것이다.  
  
그래서 __한조각 한조각부터 정렬된 배열을 만들어주는거다__  
<a href="https://imgur.com/pkxbiSh"><img src="https://i.imgur.com/pkxbiSh.png" title="source: imgur.com" /></a>  

이 작은 한조각부터 합쳐간 값을 최종적으로 리턴한다!  
  
___
## 자바스크립트 코드  
<div class="colorscripter-code" style="color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#272727;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #4f4f4f"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#aaa;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div><div style="line-height:130%">3</div><div style="line-height:130%">4</div><div style="line-height:130%">5</div><div style="line-height:130%">6</div><div style="line-height:130%">7</div><div style="line-height:130%">8</div><div style="line-height:130%">9</div><div style="line-height:130%">10</div><div style="line-height:130%">11</div><div style="line-height:130%">12</div><div style="line-height:130%">13</div><div style="line-height:130%">14</div><div style="line-height:130%">15</div><div style="line-height:130%">16</div><div style="line-height:130%">17</div><div style="line-height:130%">18</div><div style="line-height:130%">19</div><div style="line-height:130%">20</div><div style="line-height:130%">21</div><div style="line-height:130%">22</div><div style="line-height:130%">23</div><div style="line-height:130%">24</div><div style="line-height:130%">25</div><div style="line-height:130%">26</div><div style="line-height:130%">27</div><div style="line-height:130%">28</div><div style="line-height:130%">29</div><div style="line-height:130%">30</div><div style="line-height:130%">31</div><div style="line-height:130%">32</div><div style="line-height:130%">33</div><div style="line-height:130%">34</div><div style="line-height:130%">35</div><div style="line-height:130%">36</div><div style="line-height:130%">37</div><div style="line-height:130%">38</div><div style="line-height:130%">39</div><div style="line-height:130%">40</div><div style="line-height:130%">41</div><div style="line-height:130%">42</div><div style="line-height:130%">43</div><div style="line-height:130%">44</div><div style="line-height:130%">45</div><div style="line-height:130%">46</div><div style="line-height:130%">47</div><div style="line-height:130%">48</div><div style="line-height:130%">49</div><div style="line-height:130%">50</div><div style="line-height:130%">51</div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#999999">//&nbsp;오름차순&nbsp;된&nbsp;배열을&nbsp;합쳐주는&nbsp;함수</span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">function</span>&nbsp;merge&nbsp;(arr1,&nbsp;arr2){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#999999">//&nbsp;결과배열을&nbsp;선언한다.</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#999999">//&nbsp;두&nbsp;배열모두&nbsp;길이가&nbsp;0이&nbsp;아닐동안&nbsp;&nbsp;</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//&nbsp;각배열의&nbsp;0번째&nbsp;인덱스를&nbsp;비교한다.&nbsp;&nbsp;</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//&nbsp;더&nbsp;작은값을&nbsp;*꺼내서&nbsp;(shift해야됨)&nbsp;결과배열에&nbsp;푸쉬한다.&nbsp;&nbsp;</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#999999">//&nbsp;arr1의&nbsp;길이가&nbsp;0이&nbsp;아닐동안&nbsp;&nbsp;</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//&nbsp;각&nbsp;배열의&nbsp;0번째&nbsp;인덱스를&nbsp;꺼내서&nbsp;결과배열에&nbsp;푸쉬한다.</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#999999">//&nbsp;arr2의&nbsp;길이가&nbsp;0이&nbsp;아닐동안</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#999999">//&nbsp;마찬가지로&nbsp;각&nbsp;배열의&nbsp;0번째&nbsp;인덱스를&nbsp;꺼내서&nbsp;결과배열에&nbsp;푸쉬한다.</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#999999">//&nbsp;합쳐진&nbsp;결과배열을&nbsp;리턴한다.&nbsp;&nbsp;</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#ff3399">const</span>&nbsp;result&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;[];</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#ff3399">while</span>(arr1.<span style="color:#4be6fa">length</span>&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">&amp;</span><span style="color:#aaffaa"></span><span style="color:#ff3399">&amp;</span>&nbsp;arr2.<span style="color:#4be6fa">length</span>){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">if</span>(arr1[<span style="color:#c10aff">0</span>]&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">&lt;</span>&nbsp;arr2[<span style="color:#c10aff">0</span>]){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;result.push(arr1.shift())</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;}<span style="color:#ff3399">else</span>{</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;result.push(arr2.shift())</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#ff3399">while</span>(arr1.<span style="color:#4be6fa">length</span>){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;result.push(arr1.shift())</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#ff3399">while</span>(arr2.<span style="color:#4be6fa">length</span>){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;result.push(arr2.shift())</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#ff3399">return</span>&nbsp;result;</div><div style="padding:0 6px; white-space:pre; line-height:130%">}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#999999">//test</span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#4be6fa">console</span>.log(merge([<span style="color:#c10aff">1</span>,&nbsp;<span style="color:#c10aff">3</span>,&nbsp;<span style="color:#c10aff">4</span>],&nbsp;[<span style="color:#c10aff">2</span>,&nbsp;<span style="color:#c10aff">5</span>,&nbsp;<span style="color:#c10aff">9</span>]))</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">function</span>&nbsp;mergeSort&nbsp;(arr){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#999999">//&nbsp;만약&nbsp;배열의&nbsp;길이가&nbsp;1이면&nbsp;배열을&nbsp;리턴한다.</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#ff3399">if</span>(arr.<span style="color:#4be6fa">length</span>&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span><span style="color:#aaffaa"></span><span style="color:#ff3399">=</span><span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#c10aff">1</span>)<span style="color:#ff3399">return</span>&nbsp;arr;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#999999">//&nbsp;배열을&nbsp;두동강&nbsp;내서&nbsp;좌&nbsp;우로&nbsp;구분시킨다.&nbsp;&nbsp;</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#ff3399">const</span>&nbsp;standard&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;<span style="color:#4be6fa">parseInt</span>(arr.<span style="color:#4be6fa">length</span>&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">/</span>&nbsp;<span style="color:#c10aff">2</span>);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#ff3399">const</span>&nbsp;left&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;arr.slice(<span style="color:#c10aff">0</span>,&nbsp;standard);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#ff3399">const</span>&nbsp;right&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;arr.slice(standard);</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#999999">//&nbsp;좌&nbsp;우&nbsp;각각&nbsp;mergeSort시키고&nbsp;merge한&nbsp;값을&nbsp;리턴한다.</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#ff3399">return</span>&nbsp;merge(mergeSort(left),&nbsp;mergeSort(right));</div><div style="padding:0 6px; white-space:pre; line-height:130%">}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#999999">//test</span></div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#4be6fa">console</span>.log(mergeSort([<span style="color:#c10aff">5</span>,&nbsp;<span style="color:#c10aff">9</span>,&nbsp;<span style="color:#c10aff">4</span>,&nbsp;<span style="color:#c10aff">1</span>,&nbsp;<span style="color:#c10aff">6</span>,&nbsp;<span style="color:#c10aff">3</span>,&nbsp;<span style="color:#c10aff">2</span>,&nbsp;<span style="color:#c10aff">8</span>,&nbsp;<span style="color:#c10aff">7</span>]))</div></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none;color:white"><span style="font-size:9px;word-break:normal;background-color:#4f4f4f;color:white;border-radius:10px;padding:1px">cs</span></a></td></tr></table></div>  

  

### OUTPUT
<a href="https://imgur.com/jLuBukt"><img src="https://i.imgur.com/jLuBukt.png" title="source: imgur.com" /></a>  