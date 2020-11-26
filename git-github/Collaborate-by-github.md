# Solo week sprint Part1 github  
솔로위크를 더 알차게 보내기 위해  
__코드스테이츠 최강 듀오 지상, 상권 합쳐서 지상권이 자체 스프린트를 진행한다!__  
  
__깃헙 레포지토리__ : https://github.com/sleepybird96/solo-week-sprint-vanillaJS  
__코공(이상권)블로그__ : https://velog.io/@rnrel11

___

# github으로 협업하기  
코드스테이츠는 코플릿도 활용하지만,  
깃과 깃헙을 활용해 과제를 제출한다.  
깃과 관련해 놀라운 기능을 발견했으니 바로 브랜치라는 개념이다.  
상권햄과 함께 알아보자.  

## 로컬 레포지토리 만들기  
우선 gittest라는 폴더에 __git init__ 을 해서 git이 관리해줄 디렉토리를 만든다.  
### git init  

<a href="https://imgur.com/9O7ccY4"><img src="https://i.imgur.com/9O7ccY4.png" title="source: imgur.com" /></a>  

## 커밋할 파일 생성  
첫 레포 국룰인 README.MD라던지  
__연습용으로 txt하나만들어준다.__  
그리고 __add후 커밋한다.__  
__커밋 메세지는 -m'add test.txt'__ 라고 지어준다.  

그러면 현재 상태는,  
<a href="https://imgur.com/by58S9d"><img src="https://i.imgur.com/by58S9d.png" title="source: imgur.com" /></a>  

## 리모트(github) 레포지토리 생성  
<a href="https://imgur.com/X3ftFuw"><img src="https://i.imgur.com/X3ftFuw.png" title="source: imgur.com" /></a>  

## 로컬레포지토리와 연결  
git remote add origin {주소} 명령어를 써서 연결해준다.  
<a href="https://imgur.com/RZIWPzP"><img src="https://i.imgur.com/RZIWPzP.png" title="source: imgur.com" /></a>

## 협동할 브랜치인 dev브랜치 생성하기  
명령어는 git branch dev이다.  
git checkout dev로 브랜치를 이동 후,  
같이 작업할 파일의 초안정도를 구상하고 애드 후 커밋한다.  
<a href="https://imgur.com/PmhjHlv"><img src="https://i.imgur.com/PmhjHlv.png" title="source: imgur.com" /></a>  
요러한 대본작업을 한다치자.

### git commit -m'add wireframe'  
<a href="https://imgur.com/OFhzuP2"><img src="https://i.imgur.com/OFhzuP2.png" title="source: imgur.com" /></a>  

보면 master에서 가지가 하나 더 쳐진후 head가 최신커밋으로 옮겨졌다  

### master브랜치에서 git push  
<a href="https://imgur.com/fCDmMYL"><img src="https://i.imgur.com/fCDmMYL.png" title="source: imgur.com" /></a>

전체 커밋상태가 동기화 됨.  

## 상권이 형에게 대본수정을 같이하자고 하자.  
<a href="https://imgur.com/p8INdwt"><img src="https://i.imgur.com/p8INdwt.png" title="source: imgur.com" /></a>

<a href="https://imgur.com/pnvcbU3"><img src="https://i.imgur.com/pnvcbU3.png" title="source: imgur.com" /></a>

<a href="https://imgur.com/e7nR4W0"><img src="https://i.imgur.com/e7nR4W0.png" title="source: imgur.com" /></a>  

상권이 형도 이제 이 레포지토리의 콜라보레이터다.  

### 상권이 형이 포크 후 git clone  
<a href="https://imgur.com/zPC0uJr"><img src="https://i.imgur.com/zPC0uJr.png" title="source: imgur.com" /></a>  


## 지상이가 지상이 대사를 상권이가 상권이 대사를 수정  
위와같이 리모트, 지상, 상권의 동기화가 끝났다면,  
열심히 협동하여 서로의 대사를 수정할 일만 남았다.  
### 지상이가 feature/2ndLine 브랜치를 만듬  
그리고 대사를 수정하고 커밋하고 푸쉬하자.  
<a href="https://imgur.com/fBn7g5m"><img src="https://i.imgur.com/fBn7g5m.png" title="source: imgur.com" /></a>  
<a href="https://imgur.com/u9dIcur"><img src="https://i.imgur.com/u9dIcur.png" title="source: imgur.com" width ='50%'/></a>  

가지가 하나 더 쳐진채 커밋됐고  

<a href="https://imgur.com/ZOpG9SJ"><img src="https://i.imgur.com/ZOpG9SJ.png" title="source: imgur.com" width ='50%'/></a>  
리모트에도 성공적으로 연동됐다.  

### 상권이가 feature/1stLine 브렌치를 만듦  
그리고 상권이는 대사를 수정하고 커밋했다..!

<a href="https://imgur.com/MAKvrLy"><img src="https://i.imgur.com/MAKvrLy.png" title="source: imgur.com" /></a>
<a href="https://imgur.com/TwqzCwK"><img src="https://i.imgur.com/TwqzCwK.png" title="source: imgur.com" width = '50%'/></a>

그런데 상권이형은 장난끼가 발동해 내 대사까지 수정했다.  
그리고 싱글벙글 푸쉬해버렸다.  

<a href="https://imgur.com/orAm3OI"><img src="https://i.imgur.com/orAm3OI.png" title="source: imgur.com" /></a>

그리고 거기다 더해서  
나와 상의도 안하고 dev와 merge해버리는 불상사를 저지른다.  

### 현재 dev안에잇는 대본 내용  
merge를 하게되면 상위 브랜치에 하위브랜치의 커밋내용을 적용시킨다.
<a href="https://imgur.com/Y8FhPBA"><img src="https://i.imgur.com/Y8FhPBA.png" title="source: imgur.com" /></a>

### 영문도 모른체, 풀리퀘를 하러가는 지상 하지만..  
<a href="https://imgur.com/7dOQci0"><img src="https://i.imgur.com/7dOQci0.png" title="source: imgur.com" /></a>

??!

### 적잖이 당황했겠지만  pull을 한 후 직접 선 merge 후 풀리퀘를 한다  
사실 이런장난은 별거 아니다.  
<a href="https://imgur.com/gEv9fdD"><img src="https://i.imgur.com/gEv9fdD.png" title="source: imgur.com" /></a>  
그저 먼저 로컬에서 pull로 받아온 후 머지를 먼저 해보면 된다.  
그러고 상권이 형의 장난을 귀엽게 봐주고 내 대사를 한줄 더 추가한후 커밋푸쉬한다.


## 충돌을 줄이는 법 정리  
* 로컬에서 선머지 후 풀리퀘스트
* 수시로 Pull해서 상위브랜치의 상태를 보자.
* 풀리퀘가 올라올때 유심히 보자

___  
스프린트 계획: https://sleepybird.tistory.com/120  
다음편 보기: https://sleepybird.tistory.com/123