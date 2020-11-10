# reduce method
___  
리듀스 메소드는  
페어와 함께 과제풀이중,  
제대로 사용법을 익힌 메소드인데,  
이것에 대한 정리가 부족하다고 느껴서,  
한번 정리해보려고 한다.
___
</br>

## How to use reduce

</br>

리듀스는 배열을 대상으로 한 메소드다.
다른 함수 메소드와 비슷하게,  
메소드 괄호 안에 함수를 갖는다.  

</br>  

```javascript
const arr = [1, 2, 3, 4, 5]
let reducePlate = arr.reduce(function(acc, cur){
 return acc + cur;
}, 0)
```  
<a href="https://imgur.com/4LhPs9s"><img src="https://i.imgur.com/4LhPs9sm.png" title="source: imgur.com" /></a>

기본구조다.  
acc와 cur은 임의로 정할 수 있는 매개변수다.  
__acc는 누적값__  
__cur은 현재값__ 이다  
반복문과 유사하지 않은가?  
reduce안 함수블록이 끝나는곳 쉼표는  
__초기값__ 이다.  
reducePlate에는 arr의 모든요소를 __순서대로 더한 값__ 이 나온다

</br>

위 reduce메소드를 반복문으로 바꿔보면?  
```javascript
const arr = [1, 2, 3, 4, 5]
let acc = 0; //acc 인 누적값에 초기값을 0으로 설정
for(let cur of arr){
  acc = acc + cur; //계속 누적해서 cur값을 더해준다.
}
console.log(acc); //결과는 배열의 첫요소부터 끝까지 더한 수가 나온다.
```
<a href="https://imgur.com/zaRKKOf"><img src="https://i.imgur.com/zaRKKOfm.png" title="source: imgur.com" /></a>  


</br>

## 왜 for문처럼 acc에 따로 재할당안해도 값이 쌓이죠?  
</br>

재할당 하는 역할을 __return__ 이 하기 때문이다.  

### return을 빼보자.  
```javascript
let str = '누적중...누적완료..결과송출'
let 누적 = Array.from(str) 
//이 짓을 하는 이유는 reduce는 배열에만 적용되기 때문이다.
let reducePlate = 누적.reduce(function(acc, cur){
    acc + cur;
    console.log(acc)
})
```  
<a href="https://imgur.com/NZpdz4b"><img src="https://i.imgur.com/NZpdz4bm.png" title="source: imgur.com" /></a>

이렇게 뜨는 이유는 첫번째 인자인 acc에는  
__return으로 누적된 값이 재할당되기 때문이다__  
첫번째 acc에 누가 나온 이유는  
__자동으로 첫번째 요소를 acc에 할당하기 때문이다.__  
물론 연산식에 return을 넣지 않고 누적을 시킬 수 있다.
```javascript
let reducePlate = 누적.reduce(function(acc, cur){
    acc = acc + cur;
    return acc;
})
```
<a href="https://imgur.com/rtBKgcg"><img src="https://i.imgur.com/rtBKgcgm.png" title="source: imgur.com" /></a>


됨!!  
그런데 굳이 이렇게 쓸 필요가 있을까?  
```javascript
let reducePlate = 누적.reduce(function(acc, cur){
    return acc + cur;
})
```  
<a href="https://imgur.com/PUeao9P"><img src="https://i.imgur.com/PUeao9Pm.png" title="source: imgur.com" /></a>

return을 하면 리턴한 값이 acc에 쌓인다는걸 알 수 있다!  

cur값에 의문이 생기면 console로 찍어볼 수도 있다.  
```javascript
누적.reduce(function(acc, cur){
    console.log(cur)
})
```  

<a href="https://imgur.com/r8FPygc"><img src="https://i.imgur.com/r8FPygcm.png" title="source: imgur.com" /></a>


앞에 '누'를 빼먹고 적중이라고만 나온 이유는  
__0번째 요소가 자동으로 acc에 적재되기 때문이다.__









