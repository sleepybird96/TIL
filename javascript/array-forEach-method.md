# forEach 배열 메소드  

</br>

다음주에 forEach를 활용해 주어진 과제를 해결해야 한다.  
그치만 나는 한번도 forEach를 활용해 문제를 푼적이 없다(두둥)  
그래서 예습겸 MDN문서를 보며 예제 몇개를 만들려고 한다.  
그런데 놀랍도록 편한 forEach문..!  
일반 for문과 비교해 활용방안을 알아보자.  
___

</br>

## for문으로 인덱스값을 할당해줘서 순회하기  

```javascript
const fruits = ['apple', 'kiwi', 'banana', 'pineapple', 'mango', 'grape']
const fruitILike = []
for (i = 0; i < fruits.length; i++){
  if(fruits[i] === 'apple'||fruits[i] === 'banana'||fruits[i] === 'mango'||fruits[i] === 'grape'){
    fruitILike.push(fruit[si])
  }
}
console.log(fruitILike)
```  
여러개의 과일을 순회하고 내가 좋아하는 과일만 push해준다.  

<a href="https://imgur.com/EMgpq0o"><img src="https://i.imgur.com/EMgpq0o.png" title="source: imgur.com" /></a>

사실 저기있는 과일 다 좋아한다.  
가장 어렵게 만든 예제였다 정말 싫어하는 과일이 없기에..  

## forEach문으로 바꿔보자.  

```javascript
const fruits = ['apple', 'kiwi', 'banana', 'pineapple', 'mango', 'grape']
const fruitILike = []
fruits.forEach(function (fruit) {
    if(fruit === 'apple'||fruit === 'banana'||fruit === 'mango'||fruit === 'grape'){
    fruitILike.push(fruit)
  }
})
console.log(fruitILike)
```  
확연히 다른점은 __귀찮게 i를 선언해서 인덱스에 대입할 필요가없어졌다__  
하지만 인덱스 값도 필요한 경우가 있기에 그때그때 활용을 달리하는게 좋겠다.  
forEach의 강점은 그저 __함수에 매개변수하나만 두면,__  
배열을 순회하며 할당해준다는 편리함이다.
