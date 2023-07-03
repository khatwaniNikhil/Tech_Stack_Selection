# Use cases well suited for Kafka
1. event replay
2. Stream processing(native support in kafka, rabbitmq is also working to add streaming support)
3. very high throughput
4. high operational complexity is manageable
   1. requires separate zookeeper cluster
   2. storage management overhead
   3. planning partition count
   4. coordination among teams)
  
# Use cases well suited for Rabbitmq
1. complex message routing
2. minimal latency of message delivery is the focus
