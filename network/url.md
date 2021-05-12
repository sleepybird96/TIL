### Reference

[HTTP 완벽가이드](http://m.yes24.com/goods/detail/15381085)

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
그리고 웹툰 리소스 등이 있다. 네이버 하나에만 해도 수많은 리소스들이 존재하는데,  
어떻게 그 많은 서버들 중 네이버 서버에서 내가 보고싶은 웹툰 한편을 가져올 수 있을까?  
바로 인터넷의 리소스를 가리키는 표준 이름인 URL(Uniform Resource Locator)덕분이다.  
URL은 특정 리소스를 가리키고 그 리소스가 **어디에 있고 어떻게 접근할 수 있는지** 알려준다.  


## 인터넷의 리소스를 직접 탐색해보자

<img width="70%" src="https://drive.google.com/uc?id=15_QvFFdmJjdJ13uyjwnPTX1kunStb99V">

우리의 웹 브라우저(크롬, Whale 등)는 흔히들 주소창이라고 불리는 URL을 입력하는 공간이 있다. 
