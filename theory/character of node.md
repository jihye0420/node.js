Node
-----------------------
- - -
## 1. 자바스크립트 런타임
- 런타임 : 특정 언어로 만든 프로그램들을 실행할 수 있는 환경  
따라서 노드는 자바스크립트 프로그램을 컴퓨터에서 실행할 수 있게 해준다.
- 노드는 V8과 더불어 libuv라는 라이브러리를 사용한다.  
V8과 libuv는 C와 C++로 구현되어 있다.  
V8 엔진 : 오픈 소스 자바스크립트 엔진  
libuv 라이브러리 : 노드의 특성인 이벤트 기반, 논블로킹 I/O 모델을 구현하고 있다.  

| 노드의  내부구조 |
|:--------|
| Node.js Core Library |
| Node.js Bindings |
| V8와 libuv|

## 2. 이벤트 기반
- 이벤트 기반(event-driven) : 이벤트가 발생할 때 미리 지정해둔 작업을 수행하는 방식
- ex) 클릭, 네트워크 요청 등
- 이벤트 기반 시스템에서는 특정 이벤트가 발생할 때 무엇을 할지 미리 등록해두어야 한다.  
이것을 이벤트 리스너(event listener)에 콜백(callback) 함수를 등록한다고 표현한다.  
- 발생할 이벤트가 없거나 발생했던 이벤트를 다 처리하면 노드는 다음 이벤트가 발생할 때까지 대기한다.
- 이벤트 루프 : 이벤트 발생 시 호출할 콜백 함수들을 관리하고 호출된 콜백 함수의 실행 순서를 결정하는 역할을 담당한다.
- 태스크 큐 : 이벤트 발생 후 호출되어야 할 콜백 함수들이 기다리는 공간, 콜백 큐라고도 부른다.
- 백그라운드 : 타이머나 I/O 작업 콜백 또는 이벤트 리스너들이 대기하는 곳이다.

## 3. 논블로킹 I/O
- 오래 걸리는 함수를 백그라운드로 보내서 다음 코드가 실행되게 하고, 그 함수가 다시 태스크 큐를 거쳐 호출 스택으로 올라오기를 기다리는 방식
- 논블로킹 : 이전 작업이 완료될 때까지 멈추고 않고 다음 작업을 수행함을 뜻한다.
- 싱글 스레드이기 때문에 모든 코드가 이 방식으로 시간적 이득을 보기는 힘들다.
- 현재 노드 프로세스 외의 다른 컴퓨팅 자원을 사용할 수 있는 I/O 작업이 주로 시간적 이득을 많이 본다.
- I/O : Input/Output, ex) 파일 시스템 접근, 네트워크 요청
- setTimeout(콜백, 0) : 코드를 논블로킹으로 만들기 위해 사용하는 기법, 1ms의 지연 시간 존재

## 4. 싱글 스레드
- 노드는 싱글 스레드이므로 주어진 작업을 혼자서 처리해야 한다.
- 자바스크립트와 노드에서 한 번에 한 가지 일밖에 처리하지 못하므로 논블로킹이 중요하다.  
![싱글 스레드, 블로킹 모델](https://github.com/kkoon9/node.js/blob/master/img/single%20theard_blocking.PNG)  
![싱글 스레드, 논블로킹 모델](https://github.com/kkoon9/node.js/blob/master/img/single%20theard_Non_blocking.PNG)  
![멀티 스레드, 블로킹 모델](https://github.com/kkoon9/node.js/blob/master/img/multi%20theard_blocking.PNG)  
- 싱글 스레드, 블로킹 모델 : 다음 손님은 이전 손님의 요리가 나올 때까지 아무것도 못하고 기다려야 하기 때문에 매우 비효율적이다.
- 싱글 스레드, 논블로킹 모델 : 주문한 순서와 서빙하는 순서가 일치하지 않을 수 있다. 점원 혼자 많은 일을 처리할 수 있다.  
하지만 그 점원 한명이 아파서 쓰러지면 큰 문제가 발생하고 주문을 받거나 서빙을 하는데 시간이 오래 걸린다면 주문이 많이 들어 왔을 때 버거울 수 있다.
- 멀티 스레드, 블로킹 모델 : 손님의 수가 늘어날수록 점원의 수도 늘어난다. 손님의 수가 줄어들었을 때 노는 점원이 생기게 되므로 비용이 발생한다.
### 점원 여러 명이 모두 논블로킹을 쓴다면?
- 노드도 싱글 스레드 여러 개를 사용해 멀티 스레딩과 비슷한 기능을 하게 할 수 있다.
- 엄밀히 말하면 멀티 프로세싱에 가깝다.
### 프로세스와 스레드의 차이
- 프로세스 : 운영체제에서 할당하는 작업의 단위이다. 프로세스 간에는 메모리 등의 자원을 공유하지 않는다.
- 스레드 : 프로세스 내에서 실행되는 흐름의 단위이다. 하나의 프로세스는 여러 개의 스레드를 가질 수 있다. 스레드들은 부모 프로세스의 자원을 공유한다.
