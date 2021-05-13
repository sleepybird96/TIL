### Reference

[HTTP 완벽가이드](http://m.yes24.com/goods/detail/15381085)  
[[미래인터넷] URN(Uniform Resource Name) 표준 규격 업데이트 현황](http://weekly.tta.or.kr/weekly/files/20115719045730_admin.pdf)

# URL과 리소스

<img width="70%" src="https://drive.google.com/uc?id=1Qtgjl_E2HVTzCEHV9IHqs8qLdeV_IrKV">

출처 - [tutorialkart](https://www.tutorialkart.com/nodejs/split-a-url-into-readable-parts-in-node-js/)

[comment]: <> (### URL &#40;Uniform Resource Locator&#41;)

[comment]: <> (가장 널리쓰이고 흔한 행태이며 서버의 한 리소스에 대한 구체적인 **위치**를 서술한다.  )

[comment]: <> (URL은 리소스가 정확히 어디에 있고 어떻게 접근할 수 있는지 구체적으로 알려준다.  )

[comment]: <> (오늘날 대부분의 URI는 URL이다.)

[comment]: <> (<img width="80%" src="https://drive.google.com/uc?id=154Qx6MG3ckgvuY_5-Y2JfmPe3S9q3iT4">)

[comment]: <> (**네이버**에서 **webtoon**에 위치해 있는 **titleId가 602910**을 가진 리소스이다.  )

[comment]: <> (titleId만 살짝 바꾸면, 다른 웹툰을 가져오거나 유효하지 않은 웹툰이라고 할것이다.  )

[comment]: <> (위와 같이 어떻게 리소스의 정확한 위치와 접근방법을 표현하는지 상용되는 URL을 보면 알 수 있다.)

인터넷에는 수많은 서버와 그 서버 안의 리소스들이 존재한다.  
수많은 서버 중 네이버를 예시로 들어보자. 네이버에는 뉴스리소스, 이미지 리소스, 자체적인 뼈대를 구성하는 html리소스,  
그리고 웹툰 리소스 등이 있다. 네이버라는 서비스 하나에만 해도 수많은 리소스들이 존재하는데,  
어떻게 그 많은 서버들 중 네이버 서버에서 내가 보고싶은 웹툰 한편을 가져올 수 있을까?  
바로 인터넷의 리소스를 가리키는 표준 이름인 URI(Uniform Resource Identifier)덕분이다.  
URI는 감사하게도 수많은 리소스들 중 원하는 리소스를 불러올 수 있게 확실히 구분을 해준다.  
<img width="50%" src="https://drive.google.com/uc?id=1zPs--NgoeeFI-PJyIJIB13R6-j7HlcYx">

이 전 포스팅에서 설명했듯 URI는 URL이나 URN를 포괄하는 상위의 개념이다. URI는 이 두개의 부분집합으로 이루어져있다.  
URN은 현재 그 리소스가 어디에 존재하든 상관없이 그 **이름**만으로 리소스를 식별하는데 비해   
URL은 리소스가 **어디 있는지** 설명해서 리소스를 식별한다. 그러나 URN은 아직 채택이 되지않아서 접할 기회가 없었을 것이다.  
따라서 대부분의 URI는 URL을 가리킨다고 생각하면 된다.


[comment]: <> (URL은 특정 리소스를 가리키고 그 리소스가 **어디에 있고 어떻게 접근할 수 있는지** 알려준다.)


## 인터넷의 리소스를 직접 탐색해보자

<img width="70%" src="https://drive.google.com/uc?id=15_QvFFdmJjdJ13uyjwnPTX1kunStb99V">

우리의 웹 브라우저(크롬, Whale 등)는 흔히들 주소창이라고 불리는 URL을 입력하는 공간이 있다.  
URL은 앞서 말했듯 리소스가 어디 있는지 설명해서 리소스를 식별한다.  

<img src="https://drive.google.com/uc?id=12WipHh8gq6dNiMRuDuk_QpR1QAQNAdsW">

<img src="https://drive.google.com/uc?id=1v3nzQqtbJWnXh8lh-7arsm87-weo7hdC">

내가 좋아하는 웹툰 중 하나인 '연애혁명'의 URL을 간략하게 살펴보자.

### https://

위 URL의 시작인 https는 URL의 **스킴**이라는 것이다. 스킴은 웹 클라이언트가 리소스에 **어떻게** 접근하는지 알려준다.  
위와 같은 경우에는 URL이 HTTPS 프로토콜을 사용한다. HTTPS에 대해 간략히 설명하자면,  
기존 HTTP프로토콜과 똑같지만 보안적인 문제를 해결하기위해 메세지를 암호화해주는 성질을 추가한것이다.  

### comic.naver.com

두번째 부분인 comic.naver.com은 **서버의 위치**를 뜻한다. 리소스가 속해있는 서버를 알려준다.  
comic.naver.com 같은 경우에는 네이버 웹툰의 서버가 위치한 IP의 도메인이다.  

### /webtoon/detail.nhn

그리고 세 번째 부분인 /webtoon/detail.nhn은 리소스의 **경로**다.  
서버에 존재하는 리소스들 중 어떤 리소스를 요청받았는지 알려준다.  
webtoon이라는 경로에 들어가 detail.nhn에 해당하는 리소스를 가져온다.

<img src="https://drive.google.com/uc?id=1XVJOizg1M9M4wl40Lm6Df2qntprUnEpI">

위 url의 프로토콜은 HTTP가 아닌 다른 애플리케이션 프로토콜을 사용할 수도 있다.  

예를들면 ftp라는 파일전송 프로토콜을 활용할 수 있고, mailto라는 이메일 전용 프로토콜을 사용할 수 있다.  

## URL 문법

일반적으로 URL 문법은 9개 부분으로 나뉜다.

```
<스킴>://<사용자 이름>:<비밀번호>@<호스트>:<포트>/<경로>;<파라미터>?<질의>#<프래그먼트>
```
꺽새로 구분되어있는 부분 하나하나를 URL에서는 컴퍼넌트라고 한다.  
흔히 볼 수 없는것도 있을것이고, 인터넷을 개통하고나서 한번도 본적없는 컴퍼넌트도 있을것이다.  
이 모든 컴퍼넌트를 가지는 URL은 거의 없다. 각 컴퍼넌트의 역할이 무엇인지 알아보자.  

### 스킴: 사용할 프로토콜

<img src="https://drive.google.com/uc?id=1IGJwGZc-m2q9SW4g3x5MijA0dbELL69P">

스킴은 주어진 리소스에 **어떤 프로토콜을 사용해서 접근할지** 알려주는 중요한 정보다.  
위에 예시로 들어본 네이버 웹툰의 스킴은 http이다.  
스킴 컴포넌트는 알파벳으로 시작해야 하고 다음 컴퍼넌트와의 구분은 콜론과 두개의 빗금(://) 으로 구분한다.  
스킴은 대소문자를 가리지 않으므로 만약 http://www.google.com 이 아닌 HTTP://www.google.com 으로 해도  
구글에 정상적으로 접속이 되는걸 확인 할 수 있다.  

### 호스트와 포트

네트워크에서 호스트란 네트워크에 연결된 컴퓨터 혹은 그 외의 장치의 IP를 주로 의미한다.  
인터넷에 있는 리소스를 찾으려면 우선, 그 리소스가 위치한 서버가 어디있는지 알아야한다.  
이전 포스팅에서 설명했듯 서버의 위치를 찾아서 접속하게 해주는건 IP와 목적지 PORT의 역할이다.

<img src="https://drive.google.com/uc?id=1hQ29eVxBJBlda-pkBAPrbFKvQF3sT3Aj">

그 IP를 사람이 알기쉽게 바꿔준게 **도메인**이다. 결론적으로 접속하려는 서버의 IP나 도메인을 알아야한다.  
내부적으로 TCP 프로토콜을 사용하는 HTTP는 기본포트로 80을 사용하기 때문에,  
호스트 뒤에 포트를 적어주지 않아도 접속이 됐었을 것이다.  
우리가 흔히 보는 URL들은 **호스트뒤에 http포트인 80이 생략된 형태**이다.  

### 사용자 이름과 비밀번호

http에서 사용자 이름과 비밀번호를 사용하는곳은 거의없다.  
그래서 http URL은 보통 ```<사용자 이름>:<비밀번호>@``` 이 부분이 생략된 경우가 많다.  
원한다면 ```http://아무이름:아무비번@www.naver.com```으로 접속해보라 될것이다.  
보통은 기본값으로 설정되어있어서 우리가 흔히 접속하는 사이트들은 이름과 비밀번호 컴퍼넌트는 생략되어있다.  
실제로 사용하는 경우를 살펴보고싶다면 ftp프로토콜에 대해서 조사를 해보자.

### 경로

<img src="https://drive.google.com/uc?id=1r92i96SrupfFVptLC3tim1dMhXgLlBkx">

URL의 경로 컴퍼넌트는 원하는 리소스가 서버속에서 어디에 있는지 알려준다.  

<img src="https://drive.google.com/uc?id=1E2OzKckDoUbyoY7c-Z40JjK2h4tJFKWk">

이러한 위치구조는 **웹툰 폴더에 detail.nhn이라는게 있구나** 정도로만 알면된다.  
빗금'/' 으로 구분된 각각의 위치구조를 **경로조각**이라고 부르는데,  
**경로조각들은 각각 자체만의 파라미터** 컴포넌트를 가질 수 있다. 파라미터는 뭘까?  

### 파라미터

서버의 수 많은 리소스들 중 원하는 리소스를 불러올 때, 다른 형태로 불러오고 싶을 수 있다.  
불러오고 싶은 리소스가 이름과 전화번호라면, 예쁜 명함형식으로 리소스를 불러오고 싶을 수 있고,  
```이름: 졸린새, 번호: 010-1111-2222```라는 문자형태로만 불러오고 싶을 수 있다.  
또 서버 개발자 입장에서는 특정 리소스는 ```fa2Fw12b7u```같이 암호로된 토큰을 가지고있는 사람만  
접근하게 하고싶을 수 있다. 그러나 스킴과 호스트, 그리고 경로조각 만으로는 이것을 실현하기에는 불가능 하다.  
  
그래서 URL은 파라미터 컴포넌트를 가지고있는데, 이 컴퍼넌트는 **이름과 값 쌍**의 리스트를 가진다.  
즉 이 쌍을 하나만 가질 수도 있고, 여러개를 가질 수 있다.  
그런데 이 파라미터는 세미콜론(;)으로 시작하는 매트릭스 파라미터가 있고, 물음표(?)로 시작하는 쿼리파라미터가 있다.

```
http://www.name-phone.com/memberinfo/1;type=text
```


