# callback이 뭔디?  
</br>  

고차함수 문제를 풀면서,  
여러 다른 개념은 이해를 하고 문제까지 풀었다.  
각종 메소드를 활용도 하는데, 설명에서 계속 나오는  
그놈의 callback의 의미를 도통 모르겠는거다.  

</br>  

## 사전적 의미로는  
</br>  

__* 다른한수의 인자로 활용되는 함수__  
__* 어떠한 루틴이나 행위를 완료시키는 외부함수__  
__* 직역하면 다시 부른다__  

A callback function is a function passed into another function as an argument,  
which is then invoked inside the outer function to complete some kind of routine or action.  
mdn문서에서 찾아본 내용이다.  
</br>  

## 예제  

</br>  

위 사전적 의미들을 예시를 통해 알아보자.  

</br>  

### arr.map 메소드를 콜백없이 활용해 보기  
```javascript
const home = ['mother', 'father', 'sister', 'me'];
home.map(function(elements){
  console.log(elements);
}); // output 'mother' 'father' 'sister' 'me'
```  
</br>  

<a href="https://imgur.com/d4T3LgY"><img src="https://i.imgur.com/d4T3LgYm.png" title="source: imgur.com" /></a>  


</br>  

### 가족구성원을 부르는 함수를 만들어 map메소드에 콜백하기  

</br>  
한번 불렀다가 다시 부르는거라  
간절하게 불러줘야 된다.  
간절하게 느낌표 두개 더 붙여봤다.

</br>


```javascript
const home = ['mother', 'father', 'sister', 'me'];
//콜백함수로 지정해줄 가족들을 부를 함수를 만들어 준다.
function callMyFamilyBack (elements){
  console.log(elements + '!!')
}
//map 메소드에 콜백함수인 callMyFamilyBack을 호출해 인자로 넣는다.
home.map(callMyFamilyBack)
```

</br>  

<a href="https://imgur.com/kWxZNeu"><img src="https://i.imgur.com/kWxZNeum.png" title="source: imgur.com" /></a>  

</br>  

위와같이 map메소드 안에 인자로 함수를 넣어   
가족구성원을 간절하게 불러봤다.  
다양한 map이나 filter같은 __고차함수 메소드에 활용하는건 물론,__  
임의로 만든 함수안에 __인자를 함수로 필요로하는경우__  
함수를 콜백함수로 쓸것임을 __미리 정해놓고 할당한다면__  
다양한 상황에서 __비동기적으로__ 호출을 처리할 수 있다.

