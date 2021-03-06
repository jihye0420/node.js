SOPT 면접 대비 정리
-----------------------
- - -
## JavaScript란?
- 객체 기반의 스크립트 프로그래밍 언어이다.
- 웹 브라우저 내에서 주로 사용하며, 다른 응용 프로그램의 내장 객체에도 접근할 수 있는 기능을 가지고 있다.
- Node.js와 같은 런타임 환경과 같이 서버 사이트 네트워크 프로그래밍에도 사용되고 있다.
---------------------------------
### 1. 자바스크립트 런타임
- 런타임 : 특정 언어로 만든 프로그램들을 실행할 수 있는 환경  
- 노드는 V8과 더불어 libuv라는 라이브러리를 사용한다. 
### 2. 이벤트 기반
- 이벤트 기반(event-driven) : 이벤트가 발생할 때 미리 지정해둔 작업을 수행하는 방식
- 이벤트 루프 : 이벤트 발생 시 호출할 콜백 함수들을 관리하고 호출된 콜백 함수의 실행 순서를 결정하는 역할을 담당한다.
- 태스크 큐 : 이벤트 발생 후 호출되어야 할 콜백 함수들이 기다리는 공간, 콜백 큐라고도 부른다.
- 백그라운드 : 타이머나 I/O 작업 콜백 또는 이벤트 리스너들이 대기하는 곳이다.  
![event loop1](https://github.com/kkoon9/node.js/blob/master/img/eventloop1.PNG)  
![event loop2](https://github.com/kkoon9/node.js/blob/master/img/eventloop2.PNG)  
![event loop3](https://github.com/kkoon9/node.js/blob/master/img/eventloop3.PNG)  
### 3. 논블로킹 I/O
- 오래 걸리는 함수를 백그라운드로 보내서 다음 코드가 실행되게 하고, 그 함수가 다시 태스크 큐를 거쳐 호출 스택으로 올라오기를 기다리는 방식
- 논블로킹 : 이전 작업이 완료될 때까지 멈추고 않고 다음 작업을 수행함을 뜻한다.
### 4. 싱글 스레드
- 노드는 싱글 스레드이므로 주어진 작업을 혼자서 처리해야 한다.
- 자바스크립트와 노드에서 한 번에 한 가지 일밖에 처리하지 못하므로 논블로킹이 중요하다.  
### 프로세스와 스레드의 차이
- 프로세스 : 운영체제에서 할당하는 작업의 단위이다. 프로세스 간에는 메모리 등의 자원을 공유하지 않는다.
- 스레드 : 프로세스 내에서 실행되는 흐름의 단위이다. 하나의 프로세스는 여러 개의 스레드를 가질 수 있다. 스레드들은 부모 프로세스의 자원을 공유한다.
------------------------------

## 객체지향 프로그래밍(Object-Oriented Programming, OOP)
- 모든 데이터를 객체 취급하고 처리 요청을 받은 객체가 자기 안에 있는 기능을 가지고 처리한다.
- 클래스와 객체, 메서드 그리고 메시지로 이루어져 있다.

## OOP의 구성요소
### 1. 클래스
- 같은 종류의 집단에 속하는 속성과 행위를 정의한 것으로 객체지향 프로그램의 기본적인 사용자 정의 데이터형이라고 할 수 있다.
### 2. 객체
- 클래스의 인스턴스(실제로 메모리상에 할당된 것)이다.
- 객체는 고유의 속성을 가지며 클래스에서 정의한 행위를 수행할 수 있다.
- 객체의 행위는 클래스에 정의된 행위에 대한 정의를 공유함으로써 메모리를 경제적으로 사용한다.
[[TIP]]
인스턴스 : 실행 중인 임의의 프로세스, 클래스의 현재 생성된 오브젝트를 가리킨다.
[[/TIP]]
### 3. 메서드, 메시지
- 클래스로부터 생성된 객체를 사용하는 방법으로서 객체에 명령을 내리는 메시지라 할 수 있다.
- 메서드는 한 객체의 서브루틴 형태로 객체의 속성을 조작하는데 사용된다.

## OOP의 장점
- S/W의 질을 향상시키기 위해 강한 응집력과 약한 결합력을 지향해야 한다.
- 클래스에 하나의 문제 해결을 위한 데이터를 모아 놓은 데이터형을 사용함으로써 응집력을 강화한다.
- 클래스간에 독립적으로 디자인함으로써 결합력을 약하게 할 수 있다.

## OOP의 특징
- 자료 추상화, 상속, 다형성, 동적 바인딩
### 1. 자료 추상화
- 불필요한 정보는 숨기고 중요한 정보만을 표현함으로써 프로그램을 간단히 만드는 것
- 추상 자료형은 자료형의 자료 표현과 연산을 캡슐화한 것으로 접근 제어를 통해서 자료형의 정보를 은닉할 수 있다.
- OOP에서 일반적으로 추상 자료형을 클래스, 인스턴스를 객체, 연산을 메소드, 메소도의 호출을 생성자라고 한다.
### 2. 상속
- 새로운 클래스가 기존의 클래스의 자료와 연산을 이용할 수 있게 하는 기능이다.
- 상속을 통해서 기존의 클래스를 상속받은 하위 클래스를 이용해 프로그램의 요구에 맞추어 클래스를 수정할 수 있다.
- 클래스 간의 종속 관계를 형성함으로써 객체를 조직화할 수 있다.
### 3. 다형성
- 어떤 한 요소에 여러 개념을 넣어 놓은 것으로 오버라이딩이나 오버로딩을 의미한다.
- 오버라이딩 : 같은 이름의 메소드가 여러 클래스에서 다른 기능을 하는 것
- 오버로딩 : 같은 이름의 메소드가 인자의 개수나 자료형에 따라서 다른 기능을 하는 것
- 다형성을 통해서 프로그램 안의 객체 간의 관계를 조직적으로 나타낼 수 있다.
### 4. 동적 바인딩
- 실행 시간 중에 일어나거나 실행 과정에서 변경될 수 있는 바인딩
- 정적 바인딩 : 컴파일 시간에 완료되어 변화하지 않는 바인딩
- 프로그램의 한 개체나 기호를 실행 과정에 여러 속성이나 연산에 바인딩함으로써 다형 개념을 실현한다.
-------------------------------------------------------

## 함수형 프로그래밍(Functional Programming)
-------------------------------------------------------

## 동기와 비동기, 블록, 논블록
![참고](https://github.com/kkoon9/node.js/blob/master/img/synchronous_block.PNG)  
### 동기(synchronous : 동시에 일어나는)
- 동기는 말 그대로 동시에 일어난다는 뜻이다.
- 요청과 그 결과가 동시에 일어난다.
- 요청을 하면 시간이 얼마나 걸리던지 요청한 자리에서 결과가 주어져야 한다.
### 장점
- 설계가 매우 간단하고 직관적이다.
### 단점
- 결과가 주어질 때까지 아무것도 못하고 대기해야 한다.
### 비동기(Asynchronous : 동시에 일어나지 않는)
- 비동기는 동시에 일어나지 않는다는 뜻이다.
- 요청과 결과가 동시에 일어나지 않을거라는 약속이다.  
즉, 노드 사이의 작업 처리 단위를 동시에 맞추지 않아도 된다는 뜻이다.
### 장점
- 결과가 주어지는데 시간이 걸리더라도 그 시간 동안 다른 작업을 할 수 있으므로 자원을 효율적으로 사용할 수 있다.
### 단점
- 동기보다 복잡하다.
### 블록(block)
- A라는 함수를 호출했을 때, 기대하는 행위를 모두 끝마칠때까지 기다렸다가 리턴되면, 이것은 블로킹되었다고 한다.
### 논블록(Non-block)
- A라는 함수를 호출했을 때, 기대하는 행위를 요청하고 바로 리턴되면, 이것은 논블로킹되었다고 한다.

### 블록/동기
- A는 실행되고 있다.
- B라는 일을 수행하는 함수를 호출해서 B를 시작한다. (A는 스탑)
- B라는 일이 끝나면 함수를 리턴한다.
- 동기인 이유 : A와 B는 순차적으로 진행되기 때문이다.
- 블럭인 이유 : B라는 일을 함수를 호출하고 그 일을 끝나고 나서야 리턴되므로
### 블록/비동기
- A는 B라는 일을 시킨다. 그리고 바로 리턴한다. [논블록]
- B는 일을 시작하고, A도 자신의 일을 한다.
- A는 중간에 B가 하는 일의 중간 결과 보고를 받아서 처리해야 한다.
- A는 B에게 요청을 해서 중간 결과를 기다린다. [블록]
- 요청의 결과를 받고 나서 그 결과를 이용해서 자신의 일을 처리한다. 동시에 B는 또 자신의 일을 동시에 한다. [비동기]
- A는 다시 B에게 중간결과를 요청해서 기다린다. [블록]
- 요청의 결과를 받고 A는 자신의 일을, B 또한 자신의 일을 수행한다. [비동기]
[[TIP]]
1. 우체국에 가서 내가 필요한 물품은 A라고 접수원에게 말을 하고 집으로 돌아온다.
2. 우체국은 A를 준비하고, 나는 집에서 집안 청소를 한다. [비동기]
3. 우체국에 전화해서 접수원에게 A가 준비되었다고 물어본다.  
접수원은 준비될 때까지 기다리라고 한다. 나는 기다린다. [블록]
4. 접수원이 준비됐다고 말한다. 나는 우체국으로 가서 A를 가져온다.
5. 우체국은 자신의 일을 하고, 나는 A를 집으로 가져온다. [비동기]
[[/TIP]]
### 논블록/동기
- A는 B라는 일을 시킨다. 그리고 바로 리턴한다. [논블록]
- B는 일을 시작하지만 A는 일을 하지 않는다.
- A의 하는 일은 그저 B가 하는 일을 확인하는 것이다.
- B가 결과 보고(중간 보고 x)를 했는지 확인하는 함수를 호출하고 바로 리턴한다. [논블록]
- 결과 보고를 받을 때까지 기다리는 것이 아니라, 결과 보고가 나왔는지 확인하고 바로 리턴하는 것이다.
- 동기인 이유 : B가 결과보고를 하면, B는 자신의 일이 끝난 것이고 그제서야 A가 자신의 일을 하기 때문이다.
### 논블록/비동기
- A는 B의 일을 시작시키고 바로 리턴한다. [논블록]
- 그리고 A와 B는 각자 자신의 일을 한다. [비동기]
