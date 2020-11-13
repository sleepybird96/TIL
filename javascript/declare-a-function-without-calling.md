# 외부함수를 이용해 다른 외부함수의 컨텍스트에 접근하고 싶을 때  

</br>

이걸 궁금했던 이유는  
클로저 함수를 활용해,  
외부에 선언했던 변수들에 많이 접근을 해서  
문제를 해결해왔다.  
그런데 많은 함수를 만들다가 어느 순간,  
외부함수가 다른 외부함수를 참조해야되는 상황이 온것이다..!
무수히 많은 클로저를 만들면서,  
이걸 외부로 빼버리고 안쪽에서 호출해버리면 클로저마냥 외부를 참조하지 않을까? 생각했다  

### 내가 생각했던 구조  
```javascript
//변수로 할당된 버튼속성의 result element를 만들자!
function getNumberAndAlarmMe (){
  let inputNum = prompt('나 무슨숫자 생각하고 있게')
  const result = document.createElement('button')
  result.textContent = '결과확인!'
  document.querySelector('body').append(result)
  result.onclick = if5AlarmMe
}
function if5AlarmMe (){
  alert ('결과를 발표할게..')
  if(inputNum === '5'){
    alert ('두구두구..')
    alert ('딩동댕!')
  }
  return false
    alert ('두구두구..')
    alert ('땡! 다시생각해봐')
}
```  

#### 결과는?  



<a href="https://imgur.com/9GiX8xM"><img src="https://i.imgur.com/9GiX8xMm.png" title="source: imgur.com" /></a>


if5AlarmMe 함수가 inputNum을 참조할 수 없다고 한다..  
사실 함수를 조금만 배워도 당연한 문제였다.  
클로저를 배우면서 살살 녹은 내뇌가 판단력을 흐트렸다.  
그래서 코드스테이츠 헬프데스크에 물어봤다..!  
당연히 외부끼리 참조할 때에는 __매개변수__ 가 필요하다.  
그렇지만 매개변수를 넣어서 참조해버리면?

```javascript
//변수로 할당된 버튼속성의 result element를 만들자!
function getNumberAndAlarmMe (){
  let inputNum = prompt('나 무슨숫자 생각하고 있게')
  const result = document.createElement('button')
  result.textContent = '결과확인!'
  document.querySelector('body').append(result)
  result.onclick = if5AlarmMe(inputNum)//원래는 인자가 없었다.
}
function if5AlarmMe (inputNum){//
  alert ('결과를 발표할게..')
  if(inputNum === '5'){
    alert ('두구두구..')
    alert ('딩동댕!')
  }
  return false
    alert ('두구두구..')
    alert ('땡! 다시생각해봐')
}
```  

결과확인 버튼을 누르지도 않았는데 
이렇게 알람이 떠버린다.

<a href="https://imgur.com/8pxHS2d"><img src="https://i.imgur.com/8pxHS2dm.png" title="source: imgur.com" /></a>


이유는 __인자를 받으면서,__  
__함수를 실행시켜벼렸기 때문이다__  
이상황쯤 되면 욕나온다.  
예제는 저렇게 간단해 보이지만,  
내가처한 문제는 __트위틀러__ 였기 때문이다 ㅡㅡ  

## 인자를 받으면서 함수가 미리 호출되는 것을 막는법  

</br>

해답은 간단했다.  
인자를 넣은 함수를 __함수로 한번 더 감싸주면 된다!!!__  

```javascript
//변수로 할당된 버튼속성의 result element를 만들자!

function getNumberAndAlarmMe (){
  let inputNum = prompt('나 무슨숫자 생각하고 있게')
  const result = document.createElement('button')
  result.textContent = '결과확인!'
  document.querySelector('body').append(result)
  result.onclick = function(){
    return if5AlarmMe(inputNum)//함수로 한번 더 감싸준 모습
  }
}
function if5AlarmMe (inputNum){//
  alert ('결과를 발표할게..')
  if(inputNum === '5'){
    alert ('두구두구..')
    alert ('딩동댕!')
  }
  return false
    alert ('두구두구..')
    alert ('땡! 다시생각해봐')
}
```  
차이를 모르겠다고?  
```javascript
  result.onclick = function(){
    return if5AlarmMe(inputNum)//함수로 한번 더 감싸준 모습
  }
```
보다시피 함수로 한번 더 감싸주고, 인자를 넣은 함수를 리턴하면  
원하는 방식대로 코드를 만들 수 있다.  

<a href="https://imgur.com/XF7Jw8N"><img src="https://i.imgur.com/XF7Jw8Nm.png" title="source: imgur.com" /></a>

<br/>

편-안

