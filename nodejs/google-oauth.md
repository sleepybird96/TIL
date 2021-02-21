# react와 nodejs로 google로그인창 만들기(google OAuth2.0)

우리는 회원가입할 때 소셜로그인 없이는 도무지 귀찮아서 살수없는 지경에 이르렀다.  
OAuth2.0의 특혜를 삶속에서 톡톡히 느끼고있는데,  
내 프로젝트에도 적용할려고 google OAuth에 대해 알아보는데 생각보다 자료가 많지않아서,  
꽤나 애먹었다. 결국에 가장 도움이 됐던건 공식문서였다.  
공식문서를 토대로 어떻게 google OAuth를 했는지 차근차근 알아보자.

---

# OAuth 2.0의 개괄적인순서

OAuth 2.0은 서버나 클라이언트 특정 부분에서만 진행하는게 아니다.  
클라이언트에서 OAuth서버인 구글에 권한을 요청해야할 뿐더러,  
서버에서도 구글에 데이타를 요청해야한다.  
이해가 쉽게 전체적인 순서대로 설명을 작성하고, 코드또한 순서대로 작성해보자.

## 클라이언트에서 OAuth(구글)서버에 authorizationCode를 요청한다.

클라이언트에서 authorizationCode를 요청한다고? 뭔말이야 할 수있다.  
<a href="https://imgur.com/xpLFe4v"><img src="https://i.imgur.com/xpLFe4v.png" title="source: imgur.com" /></a>

바로 이 순간에 요청이 일어나는거다. 이걸 클릭하는 순간,  
요청url로 바로 이동한다. 그런데 이 요청url은 어떤클라이언트도 접속할수있냐?  
아니다. api를 등록할때 **등록했던 클라이언트 도메인만** 가능하다.  
<a href="https://imgur.com/8fXOchy"><img src="https://i.imgur.com/8fXOchy.png" title="source: imgur.com" /></a>

## OAuth서버(구글)에서 authorizationCode를준다.

그걸 어케주노? 할수도 있다.  
authorizationCode를 주게 허용하는 주체는 바로 무수히 많은 사이트를  
소셜로그인으로 이용했던 바로 당신(유저)이다.  
<a href="https://imgur.com/NeE2nL1"><img src="https://i.imgur.com/NeE2nL1.png" title="source: imgur.com" /></a>  
바로 이 과정이다.  
똑똑한 사람들은 내가 승인하는거까진 알겠는데,  
도대체 클라이언트는 어떻게 authorization코드를 받는거야? 할 수 있다.  
그건 바로바로  
<a href="https://imgur.com/9ifzGHP"><img src="https://i.imgur.com/9ifzGHP.png" title="source: imgur.com" /></a>  
홈페이지 주소창으로 세겨준다 ㅋㄷㅋㄷ 지금은 물론 안세겨져있다.  
만약에 내가 네이버를 만든사람인데 구글로그인을 만들었다치자, (???)  
api설정에서 리디렉트 도메인을 www.naver.com 으로 해놨다면,  
유저가 저 계정선택을 해서 권한을 승인한 순간,  
www.naver.com/code=대충권한코드 로 재연결해준다.  
재연결해주는 순간, 코드를 작성하는 당신은 **url로부터 저 권한코드를 따내야한다.**

## 받은 authorizationCode를 서버에다가 갖다주기

이 authorizationCode를 **서버에다 갖다준다.**  
왜갖다 주냐는 생각 말고, 일단은 갖다준다고 생각해라.  
군말없이 갖다주자.  
<a href="https://imgur.com/wotZOmV"><img src="https://i.imgur.com/wotZOmV.png" title="source: imgur.com" /></a>

## 서버는 받은 authorizationCode를 토대로 토큰을 요청한다.

토큰을 어디다 요청하냐? 감이잡힐것이다.  
당연히 서버에서 jwt를 만드는건 절대아니다!  
구글형님한테 저 권한코드도 받았는데, 토큰좀 주십쇼! 하고 요청해야한다.
<a href="https://imgur.com/4fQNDeK"><img src="https://i.imgur.com/4fQNDeK.png" title="source: imgur.com" /></a>

## OAuth(구글)는 authorization코드을 제대로 받았다면, 서버로 토큰을 준다.

<a href="https://imgur.com/87FlmLl"><img src="https://i.imgur.com/87FlmLl.png" title="source: imgur.com" /></a>

서버에서 유효한 authorization코드를 줬다면, OAuth서버에서 토큰을 준다.

토큰을 받으면 성공적으로 OAuth인증 처리가 되었다.  
그런데, 이 토큰을 어떻게 복호화하냐? 궁금할거다.

---

2편에서 계속...
