메시지 큐(Message Queue)
======================


## 1. 메시지 큐란?
1. 애플리케이션에서 데이터를 서로 교환할때 사용하는 통신 방법(메시지 지향 미들웨어-Message Oriented Middleware: MOM)
2. MOM을 구현한 시스템을 메시지 브로커라고 한다.

## 2. 메시지 큐의 장점
* 비동기 (Asynchronous) : 큐에 넣기 때문에 비동기적으로 처리 가능
* 비동조 (Decoupling) : 애플리케이션과 분리하여 결합도를 낮춤
* 탄력성 (Resilience) : 작업의 일부가 실패해도 전체에 영향을 주지 않음
* 중복 (Redundancy) : 여러 노드에 큐를 복제하여 실패할 경우 재실행 가능
* 보증 (Guarantees) : 작업이 처리된 것을 확인할 수 있음
* 확장성 (Scalable) : 다수의 프로세스들이 큐에 메시지를 보낼 수 있음

## 3. Pub/Sub Model
![mq_overview](/image/mq/pub&sub.png)   
메시지를 발행하는 Publisher와 구독하는 Subscriber가 있고 그 중간에서 중개하는 역할을 하는 게 브로커이다.    
이러한 모델을 사용하여 Pub/Sub간의 결합도를 낮출 수 있는데(Decoupling), 이을 통해 안정성과 확장성(Scalable)을 확보할 수 있다.
또한, 비동기적(Asynchronous)으로 처리할 수 있다.


## 4. 메시지 큐 오픈 소스
* RabbitMQ
    >1. AMQT 프로토콜을 구현해 놓은 프로그램 (다른 STOMP, MQTT, HTTP 프로토콜 사용 가능)
    >2. 로컬 네트워크에 있는 여러 RabbitMQ 서버를 논리적으로 클러스터링할 수 있고, 논리적인 브로커도 가능
    >3. 관리 UI가 있어 편하게 관리 가능
    >4. 대부분의 언어와 운영체제를 지원

        AMQP는 메시지 지향 미들웨어를 위한 open standard application layer protocol이다. AMQP를 이용하면 
        다른 벤더 사이에 메세지를 전송하는 것이 가능한데 JMS(Java Message Service)가 API를 제공하는 것과 달리 
        AMQP는 wire-protocol을 제공하는데 이는 octet stream을 이용해서 다른 네트워크 사이에 데이터를 전송할 수 있는 포맷으로 이를 사용하게 된다.

* Kafka
    >1. 대용량 실시간 로그 처리에 특화된 메시징 시스템
    >2. 기존 메시징 시스템 대비 TPS(Transaction per Second)가 우수
    >3. 데이터를 유실없이 안전하게 전달하는 것이 주 목적(Falut-Tolerant)
    >4. 클러스터링 가능 및 스케일 아웃 가능

