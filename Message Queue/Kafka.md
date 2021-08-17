카프카:Apache Kafka
==================

## 1. 구조
크게 Producer, Queue, Consumer로 나눌 수 있다.
- Producer : 메시지를 보내는 프로그램
- Queue : 모든 메시지를 저장하는 큐이다. 우체통같은 역할을 수행한다.
- Consumer : 메시지 수신하는 프로그램

![mq_overview](/image/mq/mq%20overview.jpg)

producer, consumer 그리고 Broker(MQ 시스템 - RabbitMQ, Kafka)는 같은 host내에서 상주할 필요는 없고, 각각의 어플리케이션은 producer, consumer 둘 다 될수 있다.

![mq_broker](/image/mq/broker.png)

## 2. 카프카 살펴보기

