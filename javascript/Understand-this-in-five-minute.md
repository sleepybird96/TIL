# this 소속 5분만에 알아보기
this에 대해 공부를 하던 중,  
잘 이해가 가지않아 콘솔창에 여러번 찍어보며 노력해봣는데,  
그 결과 this는 __아주 미꾸라지같은 녀석이라고 생각했다.__  
그래서 이 글은 this미꾸라지설(필자가 만듦)에 입각한 글이니,  
__비유의 함정__ 에 빠지기 싫은 사람들은 뒤로가기를 누르면 된다..!  
비유를 통해 정확한 개념은 못집겠지만, 이 글을 보게된다면  
확실하게 써먹을 수 있을것이다.
___  
# this의 소속을 알아보자
this의 소속은 자기가 __속해있는 객체(배열도 됨)이다.__  
this는 잡히면 자신의 현재 소속을 밝힌다.  
하지만 __쉽게 잡히지않는다.__  

<a href="https://imgur.com/rvEeg6G"><img src="https://i.imgur.com/rvEeg6G.png" title="source: imgur.com" /></a>  

<a href="https://imgur.com/mcCkJJu"><img src="https://i.imgur.com/mcCkJJu.png" title="source: imgur.com" /></a>  

<a href="https://imgur.com/cYZN5wp"><img src="https://i.imgur.com/cYZN5wp.png" title="source: imgur.com" /></a>

몇겹을 겹치더라도 똑같다.

<a href="https://imgur.com/1E5Ossl"><img src="https://i.imgur.com/1E5Ossl.png" title="source: imgur.com" /></a>  

<a href="https://imgur.com/3JomgYD"><img src="https://i.imgur.com/3JomgYD.png" title="source: imgur.com" /></a>  

<a href="https://imgur.com/dLpMaHX"><img src="https://i.imgur.com/dLpMaHX.png" title="source: imgur.com" /></a>  

ㄹㅇ 내가그렸지만 열받는다.  

## this를 잡을 유일한 수단 function  
배열에 this를 넣어도 마찬가지고  
객체에 this를 넣어도 마찬가지로, 도망가버린다.  

하지만 __function 이라는 그물로 잡아보자__  
함수는 __this를 잡을 유일한 그물망이라 생각하자__  

this는 __그물망이 속해있는 객체를 자신의 소속이라 생각한다.__  


<a href="https://imgur.com/RuOjY1i"><img src="https://i.imgur.com/RuOjY1i.png" title="source: imgur.com" /></a>  

<a href="https://imgur.com/sb2XJzR"><img src="https://i.imgur.com/sb2XJzR.png" title="source: imgur.com" /></a>  

<a href="https://imgur.com/bQ658pT"><img src="https://i.imgur.com/bQ658pT.png" title="source: imgur.com" /></a>  

<a href="https://imgur.com/JWMhQjq"><img src="https://i.imgur.com/JWMhQjq.png" title="source: imgur.com" /></a>
  
## Arrow function는 this를 못잡는다.
예시를 들것도 없다. 못잡는다.  
하지만 화살표 함수를 사용하면서, this값을 받아오고 싶을 수 있다.  
__this가 들어있는 화살표 함수를 그물망으로 감싸주자__  

<div class="colorscripter-code" style="color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#272727;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #4f4f4f"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#aaa;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div><div style="line-height:130%">3</div><div style="line-height:130%">4</div><div style="line-height:130%">5</div><div style="line-height:130%">6</div><div style="line-height:130%">7</div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">const</span>&nbsp;obj&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;{keyinObj:&nbsp;{keyinKeyinObj:&nbsp;<span style="color:#ff3399">function</span>&nbsp;arrowCollecter(){</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#ff3399">const</span>&nbsp;arrow1&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;()<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span><span style="color:#aaffaa"></span><span style="color:#ff3399">&gt;</span><span style="color:#4be6fa">console</span>.log(`Good&nbsp;Afternoon&nbsp;<span style="color:#ff3399">from</span>`)</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;<span style="color:#ff3399">const</span>&nbsp;arrow2&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span>&nbsp;()<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span><span style="color:#aaffaa"></span><span style="color:#ff3399">&gt;</span><span style="color:#4be6fa">console</span>.log(<span style="color:#4be6fa">this</span>)</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;arrow1();</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;&nbsp;arrow2();</div><div style="padding:0 6px; white-space:pre; line-height:130%">}}}</div><div style="padding:0 6px; white-space:pre; line-height:130%">obj.keyinObj.keyinKeyinObj();</div></div><div style="text-align:right;margin-top:-13px;margin-right:5px;font-size:9px;font-style:italic"><a href="http://colorscripter.com/info#e" target="_blank" style="color:#4f4f4ftext-decoration:none">Colored by Color Scripter</a></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none;color:white"><span style="font-size:9px;word-break:normal;background-color:#4f4f4f;color:white;border-radius:10px;padding:1px">cs</span></a></td></tr></table></div>  

<a href="https://imgur.com/fkcLaBn"><img src="https://i.imgur.com/fkcLaBn.png" title="source: imgur.com" /></a>