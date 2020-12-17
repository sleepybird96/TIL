# 쉽고 편한 class가 있는데 굳이 prototype?
javascript는 __prototype기반 언어다.__  
객체지향의 4가지 특성인 캡슐화, 상속, 추상화, 다형성 등을 고려한게 아니다.  
하지만 필요성이 생긴 이후 prototype체인이라는 기술로 네가지를 구현하려고 노력하게 됐다.  
그러다 es6에서 띠용하고 class가 생겼는데,  
그렇다고 javascript가 __class기반의 언어가 된것은아니다.__  
class라는 문법은 __결국 prototype기반으로 구현된 문법적 편의기능이다.__ (영어로 syntax sugar라고한다.)  
결국 class로 인스턴스의 메소드를 만드는것 또한 함수를 생성자로 활용하는것과 같다.  

prototype 객체에 대해 더 자세히 알아보자.
___
# 함수는 태어날 때 prototype객체를 가지게된다.  
<a href="https://imgur.com/7PI2pXb"><img src="https://i.imgur.com/7PI2pXb.png" title="source: imgur.com" /></a>
<a href="https://imgur.com/bBGvqaD"><img src="https://i.imgur.com/bBGvqaD.png" title="source: imgur.com" /></a>  

전화기라는 함수를 만들었다. 함수는 인자를 넣어서 특정값을 리턴하는경우로 많이 쓰지만,  
자바스크립트에서는 __훌륭한 객체 생성자가 된다__  
바로 new연산자와 함께 사용하면 되는데, 메모리를 할당하면 거기에 객체를 만들어서,  
함수의 컨텍스트를 실행시킨다.  
<a href="https://imgur.com/e9xA5vU"><img src="https://i.imgur.com/e9xA5vU.png" title="source: imgur.com" /></a>  
  
이렇게 만들어진 객체는 출처가 생긴다.  
사실 prototype이 무슨역할을 하는지, 또 각 개체의 proto가 무얼 가르키는지 안다면,  
prototype을 이용한 상속에 대한 이해가 쉬울것이다.  
___
## __proto__는 무얼 가르킬까?
<a href="https://imgur.com/Lj68SJH"><img src="https://i.imgur.com/Lj68SJH.png" title="source: imgur.com" /></a>  
__ proto __ 는 __이 객체를 만든 함수의 prototype객체를 가리킨다__  
<a href="https://imgur.com/qD2M7K5"><img src="https://i.imgur.com/qD2M7K5.png" title="source: imgur.com" /></a> 

function 전체를 가리키는게아니라 __전화기의 prototype객체를 가리킨다.__  
<a href="https://imgur.com/75YoLLe"><img src="https://i.imgur.com/75YoLLe.png" title="source: imgur.com" /></a>  
그렇쥬?  
  
### Q.꼭 함수로 생성된 객체만 __proto__를 가리키고 있을까?  
아니다,  
전역에 객체를 하나 생성해보자.  
<a href="https://imgur.com/UyFbzPV"><img src="https://i.imgur.com/UyFbzPV.png" title="source: imgur.com" /></a>  
전역에 객체를 생성하니, 그것의 __proto__는 뭐냐, 바로 모든 객체의 시조,  
__Object__ 의 프로토타입인 __Object.prototype__ 이다.  
놀랍지 않은가? 아까 만든 전화기의 시조를 찾아보자.  
<a href="https://imgur.com/kr8vvwT"><img src="https://i.imgur.com/kr8vvwT.png" title="source: imgur.com" /></a>  

결국 이 생성자로 사용될 함수 또한 시조는 Object다 그것의 prototype을 기준으로  
전역에 있는 __모든 메모리가 할당된다.__  
  
모든 메모리가 할당된다고 한다면 의문이 들것이다.  
객체가아닌 다른타입도 __proto__를 가지게된다!  
<a href="https://imgur.com/4g0cUGT"><img src="https://i.imgur.com/4g0cUGT.png" title="source: imgur.com" /></a>  

위와같이 number타입의 원시변수인 num을 선언했더니 일어나는 일을보라!  
num의 __proto__를 자동으로 __Number.prototype에 연결해줬다.__  
  
문자열도 동일하다.  
<a href="https://imgur.com/dzQ6dw0"><img src="https://i.imgur.com/dzQ6dw0.png" title="source: imgur.com" /></a>  
  
브라우저에서 전역객체인 window는 어떨까?  
<a href="https://imgur.com/zsvXmrT"><img src="https://i.imgur.com/zsvXmrT.png" title="source: imgur.com" /></a>  
___

## prototype객체는 어떤역할을 할까?  
prototype은 함수가 생성자로 사용될 때 __링크 역할__ 을 한다.  
이 말이 무슨말인지 모르겠으면  
내가 콘솔로그로 하는짓을 보자.  

<a href="https://imgur.com/wiRDmCy"><img src="https://i.imgur.com/wiRDmCy.png" title="source: imgur.com" /></a>
  
보면 생성자로 나올 때 기본특성과 prototype객체에 __메소드를 만들어줬다.__  
<a href="https://imgur.com/FXEeNcs"><img src="https://i.imgur.com/FXEeNcs.png" title="source: imgur.com" /></a>  
  
new연산자를 활용해 한국인 한사람을 생성해보자.  

<a href="https://imgur.com/so9NEBz"><img src="https://i.imgur.com/so9NEBz.png" title="source: imgur.com" /></a>  
  
철수가 쓰는 언어는 한국어다. 그런데, 프로토타입에 저장된 함수가 실행이될까?  
<a href="https://imgur.com/yeYUOMN"><img src="https://i.imgur.com/yeYUOMN.png" title="source: imgur.com" /></a>
정상적으로 실행이된다! 왜냐면 객체는 자신의 객체에서 찾을수 없는 값이면,  
자신의 __proto__인 부모 객체의 prototype에서 찾기 때문이다!  
<a href="https://imgur.com/GnVIrPH"><img src="https://i.imgur.com/GnVIrPH.png" title="source: imgur.com" /></a>  

물론 함수에 직접적으로 메소드를 저장할 수 있다.  
<a href="https://imgur.com/g8pfUcS"><img src="https://i.imgur.com/g8pfUcS.png" title="source: imgur.com" /></a>  
이 방법의 가장 큰 문제는 뭘까?  
바로 __메모리 차이다.__  
<a href="https://imgur.com/GemLb4f"><img src="https://i.imgur.com/GemLb4f.png" title="source: imgur.com" /></a>  
보다시피 없으면 링크타고가서 greeting이라는 함수를 찾았던 한국인 철수와 달리  
__나카무라에는 함수가 들어갈 저장공간이 하나 생겨버렸다.__  
지금 보기엔 문제가 없지만 만약, 함수의 크기가 크다면, 그 함수로 객체를 생성할 때마다 __불필요한 메모리낭비가 발생__ 할 것이다.  
비유하자면, 인터넷에 치면 나오는 정보를 굳이 책을 사서 가방에 넣고다니는거와 같다.  

prototype객체는 생성되는 객체마다 메모리낭비를 줄여주는 공동 저장소가 된다.
___  
javascript에선 class를 문법적 편의기능이라고 했는데, 왜 그런걸까?  
결국 prototype기반이기 때문이다.  
<a href="https://imgur.com/bQIJ4dV"><img src="https://i.imgur.com/bQIJ4dV.png" title="source: imgur.com" /></a>  
  
보다시피 타입을 살펴보면 함수이다.  

<a href="https://imgur.com/YNYqaqF"><img src="https://i.imgur.com/YNYqaqF.png" title="source: imgur.com" /></a>  
메소드의 구성 역시 prototype에 적용했던것과 동일하다.  
  
prototype을 편하게쓰기위한 class가 나왔지만,  
기본적인 구조를 알아야 더 편하게 쓰지 않을까 생각한다.