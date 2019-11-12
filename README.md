# Kafka
Kafka Cluster With 3 Brokers Configuration Files 


1st Terminal (Run Zookeeper)
~/kafka_2.11-2.3.0/bin$
: ./zookeeper-server-start.sh ~/kafka_2.11-2.3.0/config/zookeeper.properties

2nd Terminal (Run Kafka)
~/kafka_2.11-2.3.0$
: bin/kafka-server-start.sh config/server.properties
: bin/kafka-server-start.sh config/server1.properties
: bin/kafka-server-start.sh config/server2.properties 

After you run all 3 servers, create topic with replication factor = 3 options
~/kafka_2.11-2.3.0/bin$ 
: ./kafka-topics.sh --create --zookeeper localhost:2181 --topic topic1 --replication-factor 3 --partitions 10

3rd Terminal  (Produer - Producing information/data)
~/kafka_2.11-2.3.0/bin$ 
: ./kafka-console-producer.sh --broker-list localhost:9092 --topic topic1 
: ./kafka-console-producer.sh --broker-list localhost:9093 --topic topic1
: ./kafka-console-producer.sh --broker-list localhost:9094 --topic topic1 
OR
./kafka-console-producer.sh --broker-list localhost:9092 localhost:9093 localhost:9094 --topic topic1


4th Terminal 
~/kafka_2.11-2.3.0/bin$ (Consumer)
: ./kafka-console-consumer.sh --topic topic1 --bootstrap-server localhost:9092
: ./kafka-console-consumer.sh --topic topic1 --bootstrap-server localhost:9093
: ./kafka-console-consumer.sh --topic topic1 --bootstrap-server localhost:9094
OR
bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 localhost:9093 localhost:9094 --topic topic1
