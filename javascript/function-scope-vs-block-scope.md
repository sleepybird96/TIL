  # function scope 와 block scope  
  
  앞서 블로그에서 let과 var의 차이부터 먼저 포스팅 한 적이 있다.  
  단순히 앞선 궁금증에 조사 한것이었는데 그게 뒤에 배울 __scope와 연관될 줄은 몰랐다.__  
  하지만 두 스코프의 차이는 사전적 정의보단,  
  전에 올린 포스팅을 통해 아주 쉽게 예시를 들 수 있다.  

  ___
  ## var follow function scope      
  </br>
  __var__ 는 __function scope__ 를 따른다.  
  아래 예제 코드를 살펴보자.  
 </br>
    </br>

  ```javascript
  function varIsFree(){
    var 도비 = '자유가 아니다'
    if (true) {
        var 도비 = '자유다'
        console.log(도비); //자유다
    }
    console.log(도비); //자유다 
  }
  ```

  위 코드를 보면 도비는 자유라고 나온다.  
  이 전 포스팅에선 하위 블록을 무시했다고 포스팅을 했는데,  
  그런 개념도 어느정도 맞지만,  
  var가 function의 block ('{'로 열리고 '}' 로닫기는) 만 자신을 제한하기에  
  조건문 블록에서 재할당이 되었다.   
  그렇기에 도비는 자유가 되었다.  

  ___

  ## let follow block scope

  __let__ 는 __block scope__ 를 따른다.  
  아래 예제 코드를 살펴보자.  

  ```javascript
function letIsFree(){
    let 도비 = '자유가 아니다'
    if (true) {
        let 도비 = '자유다'
        console.log(도비);
    }
    console.log(도비);
}
  ```  

  이 전 포스팅에서는 조건문 바깥에서의 도비가  
  안쪽 블록을 넘어서지 못했다고 했다.  
  </br>
  그것도 나름 내가 열심히 조사해본 결과  
  맞는 말이긴하다. 하지만  
  조건문 바깥블록의 __자유가 아닌__ 도비와  
  조건문 안쪽블록의 __자유인__ 도비가 둘다 생겨난 것이다.  
  </br>
  block scope는 '{}'로 쳐져진 모든 환경이다.  
  let은 block scope를 따르고 있기에  
  if안쪽의 도비와  
  if바깥쪽의도비,  
  어느쪽의 도비가 자유인가를 묻는게 맞는듯 하다.  





    
