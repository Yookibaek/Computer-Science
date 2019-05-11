# Node.js 관하여
- [Node.js의 비동기처리 특징](#node.js의-비동기처리-특징)
- [Node.js의 올바른 사용](#node.js의-올바른-사용)
  
- [Webpack](#webpack)

## Node.js의 비동기처리 특징
[참고사이트](http://www.nextree.co.kr/p7292/)  
노드js는 싱글스레드 기반으로 동작하는 서버이다. 동시요청이 들어올 경우, Nodejs는 비동기 방식으로 요청을 처리하게 된다.
비동기 방식이란 아래와 같이 앞의 요청을 처리하다가 Dist/Network 자원 처리문제로 대기를 하게될때, 이벤트 루프에
콜백함수를 등록해두고 제어를 다음요청으로 바로 넘기는 것을 말한다. 
![image](http://www.nextree.co.kr/content/images/2016/09/syhan_140320_node1_041.png)
장점은 io로 인한 실질적인 대기시간이 0 이라는 것이다. io대기가 발생할 경우 콜백을 걸어두고 바로 io가없는 다음
요청으로 제어를 넘기기 때문이다.  
단점은 싱글 스레드이기때문에, **하나의 요청의 처리작업 자체가 오래걸린다면** 전체 서버 처리에 영향을 준다는 것이다.
이는 Node.js의 치명적인 약점이라고 한다.

## Node.js의 올바른 사용
Node.js는 Google Chrome V8엔진기반으로 동작하며 내부의 Event Loop는 싱글스레드기반으로 비동기 메시지를 처리한다.
이러한 Event Loop는 고성능 병렬처리를 보장하도록 설계되어있다. 따라서 이벤트에 의해 처리해야할 단위의 작업이 
아주 짧은 시간 안에 처리된다면, Node.js 의 장점이 극대화된다.  
그러나, 처리작업이 CPU를 많이 소모한다든지 대용량 파일을 처리하는 작업이라면 Node.js는 독약과도 같다. 이 특징을
잘 숙지하여 프로젝트에 언어 선택을 해야 하겠다.

## 비동기 프로그래밍 기본

## Webpack
Webpack은 Entry로 지정한 노드로부터 의존성 트리를 만들고, 하나의 파일로 번들링하여 output으로 출력하는 것.
- webpack: 웹팩 핵심 패키지
- webpack-cli: 터미널에서 웹팩 커맨드 실행할 수 있게 해주는 커맨드라인 도구
[webpack이란?](http://www.daleseo.com/webpack-basics)
[webpack기본설정](http://www.daleseo.com/webpack-config/)

