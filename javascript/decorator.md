### Reference

🗂[공식문서](https://www.typescriptlang.org/docs/handbook/decorators.html)

# 타입스크립트 데코레이터

네스트나 앵귤러같은 프레임워크를 마주하다보면 심심치않게 볼수있는녀석이 있다.
<a href="https://imgur.com/euguoGG"><img src="https://i.imgur.com/euguoGG.png" title="source: imgur.com" /></a>

바로 이 골뱅이가 붙어진 '데코레이터' 라고 불리는 녀석이다.
타입스크립트에만 있는건 아니고, 자바스크립트에도 있는 기능이지만 정식기능이아닌,  
표준화 절차를 진행중인 기능이다.
그러나 타입스크립트에선 이 기능을 제공을 하고, 타입스크립트를 기반으로하는 프레임워크에서도  
이 기능을 사용하고 있다. 이미 주력 프레임워크를 nest나 앵귤러로 정했다면,  
의존성 주입이고 뭐고 이 데코레이터라는 친구의 역할부터 알아야겠다.

</br>

우선 데코레이터는 클래스, 속성, 메소드, 매개변수 앞에 붙일 수 있는 함수이다.
java의 어노테이션과 생김새가 비슷하다는데 기능은 다르다고 한다.  
자바를 몰라서 잘모르겠다 ㅎㅎ;
우선 인자를 하나 받으면 인자를 그대로 뱉어버리는 함수를 만들어보자.
함수 이름은 미러
<a href="https://imgur.com/1Estz1R"><img src="https://i.imgur.com/1Estz1R.png" title="source: imgur.com" /></a>

특정 인자를 받아 콘솔을 한번 찍고 인자를 그대로 리턴하는 함수다.

<a href="https://imgur.com/emuNx2V"><img src="https://i.imgur.com/emuNx2V.png" title="source: imgur.com" /></a>

이번엔 마법사 클래스를 만들고 위에다 아까 만든 미러를 붙여보자

<a href="https://imgur.com/FS5fjsQ"><img src="https://i.imgur.com/FS5fjsQ.png" title="source: imgur.com" /></a>

class wizzard 를 그대로 출력하는걸 볼 수 있다.

즉 이다음에 오는 클래스를 인자로 받고 받은 클래스를 통해 뭔가를 해주는 역할이라고 볼 수 있다.  
심화적으로 어떤 기능이 있고 어떻게 활용하는지 알아보자

---

## 데코레이터 합성

데코레이터도 여러개로 합성이 가능하다.  
밑에 예제를 보자.
<a href="https://imgur.com/IGxdceL"><img src="https://i.imgur.com/IGxdceL.png" title="source: imgur.com" /></a>

이렇게 중첩이 가능한데, 상단에 있을 수록 상위함수라고 나는 이해했다.  
ex) blackmirror(mirror(class Wizzard{}))

## 데코레이터 팩토리

함수 사용 시 인자를 받는 것 과 비슷하게 데코레이터 또한 인자를 받을 수 있다. 데코레이터 팩토리 함수는 데코레이터를 감싼다.  
인자가 필요한 데코레이터가 있을 때 데코레이터 팩토리로 감싸준다.

<a href="https://imgur.com/3BLTpZl"><img src="https://i.imgur.com/3BLTpZl.png" title="source: imgur.com" /></a>

위와같이 Purchase라는 행위를 데코레이터로 만들고, 인자로 돈을 받고싶다.  
그럴땐 데코레이터 함수를 한번 팩토리함수로 감싸야 인수를 받을 수 있다.

## 클래스 데코레이터

별건 없고 클래스 위에다 붙이는 데코레이터다.
클래스를 수정하거나 다른걸로 대체해버릴 수 있다.
<a href="https://imgur.com/qomAyJE"><img src="https://i.imgur.com/qomAyJE.png" title="source: imgur.com" /></a>
<a href="https://imgur.com/1ks3edr"><img src="https://i.imgur.com/1ks3edr.png" title="source: imgur.com" /></a>

데코레이터에서 재정의한 속성 및 메소드는 기존 클래스에 있던것보다 우선한다.

## 메소드 데코레이터

데코레이터는 클래스 말고도 클래스 안의 메소드에도 갖다 붙일 수 있다!  
공식문서에서는 메소드를 확인하고 수정하고 교체하는데 활용하란다  
메소드에 데코레이터가 붙으면, 데코레이터가 받게 될 인자는 총 세가지다.  
확인해보자.

<a href="https://imgur.com/sD3MmHa"><img src="https://i.imgur.com/sD3MmHa.png" title="source: imgur.com" /></a>

<a href="https://imgur.com/r7X0GRe"><img src="https://i.imgur.com/r7X0GRe.png" title="source: imgur.com" /></a>

받은 인자를 다 확인해보니 첫번째 인자로 메소드가 속한 클래스가 나오고,  
두번째 인자로는 메소드 이름이 문자열로 나온다.  
세번째 인자로 신원 미상의 세가지 불린값이 나오는데,  
이게 뭐신고? [Object.defineProperty()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Object/defineProperty)  
ES5에 나오는 메소드의 descriper 속성인데, 메소드가 forIn 문에 노출될건지나,  
재할당이 가능한지 여부를 바꿀 수 있다.  
이게 자주쓰이는가..? 몰르겠다. 허허

## 매개변수 데코레이터

nestjs를 하면 특히 많이 쓰고 보는 데코레이터다.  
생상자의 매개변수에다가 골뱅이를 무수히 달아주는데 이게 사실 뭔지몰라서  
많이 답답했다.  
지금 이 글을 쓰는순간 그냥 typeorm이나 nest의 데코레이터는  
생성자의 매개변수를 인수로 받아서 객체로 만들어 주겠거니 싶다.  
진짜 그런지 보자.

<div class="colorscripter-code" style="color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important; position:relative !important;overflow:auto"><table class="colorscripter-code-table" style="margin:0;padding:0;border:none;background-color:#272727;border-radius:4px;" cellspacing="0" cellpadding="0"><tr><td style="padding:6px;border-right:2px solid #4f4f4f"><div style="margin:0;padding:0;word-break:normal;text-align:right;color:#aaa;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="line-height:130%">1</div><div style="line-height:130%">2</div><div style="line-height:130%">3</div><div style="line-height:130%">4</div><div style="line-height:130%">5</div><div style="line-height:130%">6</div></div></td><td style="padding:6px 0;text-align:left"><div style="margin:0;padding:0;color:#f0f0f0;font-family:Consolas, 'Liberation Mono', Menlo, Courier, monospace !important;line-height:130%"><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">import</span>&nbsp;{&nbsp;Connection,&nbsp;ConnectionOptions&nbsp;}&nbsp;<span style="color:#ff3399">from</span>&nbsp;<span style="color:#ffd500">'typeorm'</span>;</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">import</span>&nbsp;{&nbsp;EntityClassOrSchema&nbsp;}&nbsp;<span style="color:#ff3399">from</span>&nbsp;<span style="color:#ffd500">'../interfaces/entity-class-or-schema.type'</span>;</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">export</span>&nbsp;<span style="color:#ff3399">declare</span>&nbsp;<span style="color:#ff3399">const</span>&nbsp;InjectRepository:&nbsp;(entity:&nbsp;EntityClassOrSchema,&nbsp;connection?:&nbsp;<span style="color:#4be6fa">string</span>)&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span><span style="color:#aaffaa"></span><span style="color:#ff3399">&gt;</span>&nbsp;(target:&nbsp;object,&nbsp;key:&nbsp;<span style="color:#4be6fa">string</span>&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">|</span>&nbsp;<span style="color:#ff3399">symbol</span>,&nbsp;index?:&nbsp;<span style="color:#4be6fa">number</span>&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">|</span>&nbsp;<span style="color:#4be6fa">undefined</span>)&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span><span style="color:#aaffaa"></span><span style="color:#ff3399">&gt;</span>&nbsp;<span style="color:#4be6fa">void</span>;</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">export</span>&nbsp;<span style="color:#ff3399">declare</span>&nbsp;<span style="color:#ff3399">const</span>&nbsp;InjectConnection:&nbsp;(connection?:&nbsp;Connection&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">|</span>&nbsp;ConnectionOptions&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">|</span>&nbsp;<span style="color:#4be6fa">string</span>)&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span><span style="color:#aaffaa"></span><span style="color:#ff3399">&gt;</span>&nbsp;ParameterDecorator;</div><div style="padding:0 6px; white-space:pre; line-height:130%"><span style="color:#ff3399">export</span>&nbsp;<span style="color:#ff3399">declare</span>&nbsp;<span style="color:#ff3399">const</span>&nbsp;InjectEntityManager:&nbsp;(connection?:&nbsp;Connection&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">|</span>&nbsp;ConnectionOptions&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">|</span>&nbsp;<span style="color:#4be6fa">string</span>)&nbsp;<span style="color:#aaffaa"></span><span style="color:#ff3399">=</span><span style="color:#aaffaa"></span><span style="color:#ff3399">&gt;</span>&nbsp;ParameterDecorator;</div><div style="padding:0 6px; white-space:pre; line-height:130%">&nbsp;</div></div><div style="text-align:right;margin-top:-13px;margin-right:5px;font-size:9px;font-style:italic"><a href="http://colorscripter.com/info#e" target="_blank" style="color:#4f4f4ftext-decoration:none">Colored by Color Scripter</a></div></td><td style="vertical-align:bottom;padding:0 2px 4px 0"><a href="http://colorscripter.com/info#e" target="_blank" style="text-decoration:none;color:white"><span style="font-size:9px;word-break:normal;background-color:#4f4f4f;color:white;border-radius:10px;padding:1px">cs</span></a></td></tr></table></div>

타입orm의 데코레이터다.  
데코레이터 팩토리로 인자를 받고 그이후를 처리하는것처럼 보인다.  
세세한 로직까진 몰라도 데코레이터가 어떤식으로 나의 class와 메소드  
그리고 속성들을 받아서 활용하는지 decorator를 많이 활용하는 프레임워크를 사용한다면  
필수적으로 알아야겠다.
