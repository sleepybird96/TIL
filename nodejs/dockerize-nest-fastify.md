# nest-fastify 앱을 dockerize해보자!

이거때문에 장장 한시간가량은 날렸다.  
우선 이번 문제는 nestjs 서버앱을 dockerize할려고 했을 때 일어난 문제였다.  
아무리 docker포트와 로컬포트를 연결해줘도 응답이 뜨질 않는거시었다.  
이게 fastify의 문제였는데,  
해석이 딸려서 왠진 모르겠다 ㅎ..  
어떻게 해결했는지 지켜보시라!

## 우선 nest앱을 만들어준다.

빠르다고 동네방네 소문난 fastify를 쓸려고하는데,  
nest의 아름다운 규칙과 함께 쓰고싶다 이말이다.  
nest앱에 fastify를 적용시키는건 증말 간단하다.  
[공식문서](https://docs.nestjs.com/techniques/performance)에서 정말 친절하게 설명돼있기 때문이다.  
아차차 혹여나볼 nest뉴비를위해 nest cli로 app부터 만들자. 나도 뉴비임 ㅎㅎ  
**nest new nest-fastify-app** 명령어를 통해 호로록 만들자.  
전역에 nest가 깔려있어야한다.

<a href="https://imgur.com/CS1hteQ"><img src="https://i.imgur.com/CS1hteQ.png" title="source: imgur.com" /></a>

그럼 이렇게 보일러플레이트 다깔아준다.  
쉽고 짱편한 nest하싈?

## nest@platform-fastify모듈을 추가해주고, 루트파일에 적용시켜주자.

<a href="https://imgur.com/DmwN5av"><img src="https://i.imgur.com/DmwN5av.png" title="source: imgur.com" /></a>

fastify는 express에비해 약 2배빠른 속도를 지녔다고한다.  
nest도 그래서 발빠르게 fastify와 호환이되게 했다.  
본래 nest는 express를 기반으로 한다.  
하지만 nest프레임워크의 기능들은 그대로 사용하면서, 앱의 기반만 fastify로 바꿀 수 있다.

<a href="https://imgur.com/Sc3B6ZX"><img src="https://i.imgur.com/Sc3B6ZX.png" title="source: imgur.com" /></a>

main.ts로 가주자.  
<a href="https://imgur.com/oBmCFgL"><img src="https://i.imgur.com/oBmCFgL.png" title="source: imgur.com" /></a>

공식문서에 나와있는대로 **불러오는 nestFactory의 생성자를 fastify로 바꿔준다**  
그리고 두번째 인자에 FastifyAddapter도 추가해준다 morgan과 같은 미들웨어를 즐겨썼다면,  
logger설정도 해준다.  
<a href="https://imgur.com/p9CrVQj"><img src="https://i.imgur.com/p9CrVQj.png" title="source: imgur.com" /></a>

그러나 여기서 당신의 서버앱을 dockerize 할려고할때!!!!!  
listen 의 두번째인자는 무조건 "0.0.0.0"으로 바꿔줘야한다!  
<a href="https://imgur.com/kNS0MhW"><img src="https://i.imgur.com/kNS0MhW.png" title="source: imgur.com" /></a>

이렇게 말이다.  
이유는 [fastify공식문서](https://www.fastify.io/docs/latest/Getting-Started/#your-first-server)에 설명이 잘돼있다.

## 프로젝트 디렉토리에 Dockerfile을 삽입해주자.

<a href="https://imgur.com/IjVyyPS"><img src="https://i.imgur.com/IjVyyPS.png" title="source: imgur.com" /></a>

**Dockerignore와 빌드단계 라인이랑 실행단계라인을 나누는건 일단은 생략하겠다 .env와같은것만이라도 ignore에넣자**  
1시간넘게 삽질한결과를 공유하고싶다 여러분은 삽질하지마세요  
그리고 docker이미지를 만들어준다.
<a href="https://imgur.com/dzpdlkz"><img src="https://i.imgur.com/dzpdlkz.png" title="source: imgur.com" /></a>

## 빌드가 다됐으면 실행해보자.

여기서 중요한점은 도커 컨테이너안에 있는 서버앱의 포트와,  
**우리의 로컬포트를 맵핑을 해줘야한다.**  
그냥 run하면 안된다는것!!!!  
<a href="https://imgur.com/UIk4lZa"><img src="https://i.imgur.com/UIk4lZa.png" title="source: imgur.com" /></a>

-p 키워드로 로컬포트를 열어주면서 컨테이너에있는 포트와 연결시켜줄 수 있다.  
여기서 로컬에서는 어떤포트를 열어줘도 상관없다 개인취향임 ㅇㅇ  
나는 4000포트가 좋다 뭔가  
<a href="https://imgur.com/2W0AcbA"><img src="https://i.imgur.com/2W0AcbA.png" title="source: imgur.com" /></a>

그럼 빌드된 js파일을 node가 실행시켜주고있는걸 확인할 수 있고,  
<a href="https://imgur.com/BUaTo9Q"><img src="https://i.imgur.com/BUaTo9Q.png" title="source: imgur.com" /></a>

get요청또한 정상적으로 받아오는걸 확인할 수 있다.  
express와 nest를 같이썼을땐 생기지않는 이슈다.  
얼마나 빠른지 한번체감해볼려고 fastify를 빌드했다가 적잖이 당황하지말고,  
핵심은 0.0.0.0으로 바꿔주자 였다.  
긴 뻘글 읽어주느라 감사
