### Reference

📋[HomoEfficio - Blocking-NonBlocking-Synchronous-Asynchronous](https://homoefficio.github.io/2017/02/19/Blocking-NonBlocking-Synchronous-Asynchronous/)  
📋[\_jbee - blocking, non-blocking and async](https://asfirstalways.tistory.com/348)  
📋[wonhee010 - 동기 vs 비동기 (feat. blocking vs non-blocking)](https://velog.io/@wonhee010/동기vs비동기-feat.-blocking-vs-non-blocking)
📼[우의 Block vs Non-Block & Sync vs Async](https://youtu.be/IdpkfygWIMk)

# 동기와 비동기 그리고 Blocking과 Non-Blocking

우선 최근 면접을 보고왔는데, 동기와 비동기에 대해 차이점을 설명해달라고 하셨다.  
답을 어떻게 했냐면, '동기는 즉각적으로 처리되는거고 비동기는 뒤로 미뤄놨다가,  
나중에 처리한다'고 대답했다.  
<a href="https://imgur.com/BkjLUV5"><img src="https://i.imgur.com/BkjLUV5.jpg" title="source: imgur.com" /></a>

말하면서는 나쁘지않게 대답을 했다고 생각했는데, 기차를 타고 집에 오면서  
곱씹으면 곱씹을수록 내 대답이 너무 구렸었다 ㄱ-  
틀린 말이 아니지만 운영체제적인 관점에서 봤을 때, 다소 미흡한 대답이지 않았나 생각했다.  
그 외에도 구린 답변이 많았지만 특히나 동기와 비동기 작업은  
개발을 한다면 평생 달고다녀야할 작업처리 방식 이기에 조금만 더 깊숙히 알아보자

## 동기와 비동기

우선 노트에다 해야할 일을 우선순위대로 쭉 적어보자  
실제로 내가 해야될 일들이다

- 빨래하기
- 방청소하기
- 침튜브보기
- 간식먹기

<a href="https://imgur.com/GYGFEMM"><img width="50%" src="https://i.imgur.com/GYGFEMM.png" title="source: imgur.com" /></a>

저 순서대로 안하면 엄마한테 혼난다.  
그런데 여기서, 빨래를한 다음 청소를 하고 청소가 끝나야 비로소  
누워서 **엄마가** 침착맨을 보게하는등 할일을 **끝낸것에 대한 간섭**이 일어난다면 **동기**다.  
그러나 침착맨부터 보고 간식도 먹으면서 집에 잔소리할 엄마도 없어서  
내가 빨래를 끝내고 청소를 끝내고 놀고있는지 간섭이 없다.. 하지만 **내마음 한구석에서 찝찝**하다면 **비동기**다.

</br>

조금 억지로 비유를 든 감이 없지않아 있지만,  
실제로 호출하는 함수가 호출되는 함수의 작업 완료 후 리턴을 기다리거나  
호출되는 함수로 부터 바로 리턴 받더라도 작업 완료 여부를  
호출**하는** 함수가 작업완료 여부를 계속해서 신경쓰면 **동기**다.  
**반면** 호출**되는** 함수에게 **callback 을 전달**하고,  
호출**되는** 함수가 작업완료 여부를 신경쓴다면, **비동기**이다.

## 블로킹과 논블로킹

아까 써먹은 할일리스트를 다시 불러와보자.

- 빨래하기
- 방청소하기
- 침튜브보기
- 간식먹기

이 글을 쓰는와중에도 방청소를 안하고있다.  
**빨래가 끝날 때 까지** 다음 리스트에 있는 방청소를 못한다다면 **블로킹**,  
빨래가 **오래걸릴것 같아서** 일단 방청소를 시작한다면 **논블로킹**이다.

</br>

이역시 조금은 억지가 있지만,  
실제로 블로킹의 스레드는 **호출 된 함수**가  
자신의 작업을 **마칠 때 까지 return을 하지않는다.**  
반면 논블로킹의 스레드는 **호출 된 함수**가 할일이 끝나지 않아도 즉시 return을 한다.

## 그래서 비동기는 논블로킹 동기는 블로킹이겟네?

아니다. 바로 차이점은 둘의 관점이다.  
**동기와 비동기**는 호출되는 **함수의 작업 완료 여부**를 **누가** 신경쓰느냐가 관점이고,  
**블로킹 논블로킹**은 호출된 함수가 **바로 return**을 하느냐 안하냐가 관점이다.  
<a href="https://imgur.com/EurPx4s"><img src="https://i.imgur.com/EurPx4s.gif" title="source: imgur.com" /></a>

그래서 IBM developerworks 에 이런 2:2매트릭스도 있다.  
얘기만 들었을 땐 절대 공존 못할거같은 블로킹과 비동기, 논블로킹과 동기가 공존한다.

### 블로킹 + 동기

호출된 함수의 작업여부는 호출한 함수가 통제를하고,  
호출된 함수 역시 자신의 할일이 종료될 때 까지 return 하지 않는다.

### 논블로킹 + 비동기

호출한 함수는 호출된 함수에게 callback을 넘겨주고,  
호출된 함수는 즉시 return을 하고 다른 작업을 할수있게 넘긴다.  
차후 과정을 거친 후 넘겨받은 callback을 다른작업이 끝난뒤 호출하거나.  
다른 작업이 진행되는 도중에 호출한다.  
nodejs는 이벤트루프의 처리 순서에따라 큐에쌓인 callback을 호출한다.

### 블로킹 + 비동기?

일단 블로킹되어 호출된함수가 return할 때 까지 다른작업을 할 수없다..  
그리고 호출된 함수는 다음 작업을 할수있게 한 후 콜백을 호출하는게 **아닌**  
블로킹 된 후 자신의 할일을 종료하고 callback을 호출한다.  
블로킹 + 동기와 크게 다를것없는 처리방식이라 잘 쓰이진 않지만,  
논블로킹 + 비동기 방식을 쓴는중 **그중 하나라도 Blocking으로 동작**하는 친구가 있다면  
블로킹 + 비동기 방식으로 처리된다.  
대표적으로 Nodejs와 MySQL의 조합이 그렇다고 한다.

### 논블로킹 + 동기?

이것도 좀 생소하지만  
호출된 함수는 바로 return하고 다음작업으로 넘겨준다.  
그리고 callback이 호출됐는지 여부를 지속해서 호출된함수에게 물어본다.  
예시로는 나는 써본적 없는 WebLogic의 Future Response model for HTTP 이 있다고 한다. [참고](https://bcho.tistory.com/224)