### Умный брокер, Тупой потребитель
RabbitMQ сам отправляет сообщения читателям(push).
### Умный получатель, тупой брокер
В Kafka читатели сами запрашивают сообщения(pull).  
### topic-partition и queue
В Kafka паралелизм и асинхроность реализованы на partition в topic, а в rabbitMQ на распределители exchange(вместо kafka cluster) и хранилищах queue.
В queue всегда FIFO, в topic FIFO только в partition.
Бляагодаря partition можно легко горизонтально маштобировать topic, с queue придётся создавать ещё одну и разделять между нимм
#### RabbitMQ
![[RabbitMQ_queue.png]]
![[RabbitMQ_queue_2.png]]
#### Apache  Kafka
![[topics_kafka.png]]

