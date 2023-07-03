# references
1. https://www.slideshare.net/Pivotal/rabbitmq-kafka
2. https://www.youtube.com/watch?v=7Faly8jORIw

# Use cases well suited for Kafka
1. event replay
2. Stream processing
   1. native support in kafka
   2. rabbitmq does not provide native support - requires using Reactor + Rabbitmq reactive api + redis store)
4. very high throughput(kafka multiple consumer groups per partition, in rabbitmq queues are single threaded)
5. massive scale (rabbitmq suffers  beyond 5 brokers)
6. high operational complexity is manageable
   1. requires separate zookeeper cluster
   2. storage management overhead
   3. planning partition count
   4. coordination among teams)
  
# Use cases well suited for Rabbitmq
1. leverage flexible message routing for complex use cases
2. priortity based processing of messages
3. minimal latency of message delivery is the focus
