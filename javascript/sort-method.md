# About array.sort() method  

</br>

underbar라는 과제를 풀다가 마지막에  
_.sortby라는 함수를 구현해야하는데,  
sort라는 메소드의 활용과,  
정확한 용도에대한 학습이 부족하다고 느껴져서  
이렇게 정리하며 복습하려 한다.  

___

## 일반적인 형태  

</br>

__정리할배열.sort(비교함수)__  
sort메소드 역시 함수를 인자로 갖기에,  
헷갈리는 부분이 많다. 하나씩 짚고 넘어가보자.  

</br>
</br>

### 비교함수가 없을경우  

<div class="colorscripter-code" style="color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#272727;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #4f4f4f"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#aaa;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">const</span>&nbsp;numArr&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;[<span style="color:#c10aff">1</span>,&nbsp;<span style="color:#c10aff">5000</span>,&nbsp;<span style="color:#c10aff">450</span>,&nbsp;<span style="color:#c10aff">9</span>,&nbsp;<span style="color:#c10aff">30000</span>,&nbsp;<span style="color:#c10aff">2500000</span>,&nbsp;<span style="color:#c10aff">6000</span>,&nbsp;<span style="color:#c10aff">70</span>];</div><div style="padding:0 6px; white-space:pre; line-height:130%">numArr.sort();</div></div><div style="text-align:right;margin-top:-13px;margin-right:5px;font-size:9px;font-style:italic"><a href="http://colorscripter.com/info#e" target="_blank" style="color:#4f4f4ftext-decoration:none">Colored by Color Scripter</a></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none;color:white"><span style="font-size:9px;word-break:normal;background-color:#4f4f4f;color:white;border-radius:10px;padding:1px">cs</span></a></td></tr></table></div>

<a href="https://imgur.com/CVJOLwA"><img src="https://i.imgur.com/CVJOLwAl.png" title="source: imgur.com" /></a>


이 근본없는 정리가 보이나?
비교함수가 없을경우 모든 요소를 스트링으로 바꿔서,  
__유니코드 순서대로 정렬한다__  

</br>
</br>

### 비교함수가 있을경우  

</br>

비교함수가 있을경우,  
그 비교함수를 기준으로 정렬한다.  

</br>

#### ! 비교함수를 받아들이는 방식  
__case1)compare(a, b)에서 리턴값이 0보다 작은경우__  
a가 b보다 __우선순위가 높다__ 고 인식한다.  
__case2)compare(a, b)에서 리턴값이 0보다 큰경우__  
a를 b보다 __우선순위가 떨어진다__ 고 인식한다.  
__case3)compare(a, b)에서 리턴값을 0으로 받은경우__  
a와 b의순서를 __동일시__ 한다. === __순서를 정의하지않는다.__  

</br>

#### ! 응용예제

<div class="colorscripter-code" style="color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#272727;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #4f4f4f"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#aaa;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div><div style="line-height:130%">3</div><div style="line-height:130%">4</div><div style="line-height:130%">5</div><div style="line-height:130%">6</div><div style="line-height:130%">7</div><div style="line-height:130%">8</div><div style="line-height:130%">9</div><div style="line-height:130%">10</div><div style="line-height:130%">11</div><div style="line-height:130%">12</div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">const</span>&nbsp;numArr&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;[<span style="color:#c10aff">1</span>,&nbsp;<span style="color:#c10aff">5000</span>,&nbsp;<span style="color:#c10aff">450</span>,&nbsp;<span style="color:#c10aff">9</span>,&nbsp;<span style="color:#c10aff">30000</span>,&nbsp;<span style="color:#c10aff">2500000</span>,&nbsp;<span style="color:#c10aff">6000</span>,&nbsp;<span style="color:#c10aff">70</span>]</div><div style="padding:0 6px; white-space:pre; line-height:130%">numArr.sort(<span style="color:#ff3399">function</span>(a,&nbsp;b){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#ff3399">if</span>(a&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">&gt;</span>&nbsp;b){&nbsp;&nbsp;<span style="color:#999999">//a가&nbsp;b보다&nbsp;크면</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">return</span>&nbsp;<span style="color:#c10aff">1</span>&nbsp;&nbsp;<span style="color:#999999">//a는&nbsp;b보다&nbsp;우선순위가&nbsp;떨어진다</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#ff3399">if</span>(a&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span><span style="color:#aaffaa"></span><span style="color:#ff3399">=</span><span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;b){&nbsp;<span style="color:#999999">//a가&nbsp;b랑&nbsp;같으면</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">return</span>&nbsp;<span style="color:#c10aff">0</span>&nbsp;&nbsp;<span style="color:#999999">//a와&nbsp;b의&nbsp;우선순위&nbsp;정하기는&nbsp;하지않는다.</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#ff3399">if</span>(a&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">&lt;</span>&nbsp;b){&nbsp;&nbsp;<span style="color:#999999">//a가&nbsp;b보다&nbsp;작으면</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;&nbsp;&nbsp;<span style="color:#ff3399">return</span>&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">-</span><span style="color:#c10aff">1</span>&nbsp;&nbsp;<span style="color:#999999">//a는&nbsp;b보다&nbsp;우선순위가&nbsp;높아진다</span></div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;}</div><div style="padding:0 6px; white-space:pre; line-height:130%">})</div></div><div style="text-align:right;margin-top:-13px;margin-right:5px;font-size:9px;font-style:italic"><a href="http://colorscripter.com/info#e" target="_blank" style="color:#4f4f4ftext-decoration:none">Colored by Color Scripter</a></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none;color:white"><span style="font-size:9px;word-break:normal;background-color:#4f4f4f;color:white;border-radius:10px;padding:1px">cs</span></a></td></tr></table></div>

<a href="https://imgur.com/tc2x7I7"><img src="https://i.imgur.com/tc2x7I7l.png" title="source: imgur.com" /></a>  

<br>

부등호를 바꾸면 오름차순도 가능하다.  
이걸단순히 외워서썼다니..!  






