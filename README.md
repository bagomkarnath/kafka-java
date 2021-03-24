# kafka Producer, Consumer in Java

Steps to runn spring boot - execute this command on root project folder 
./mvnw spring-boot:run

# Access and send message from Spring boot

 <a href=" http://localhost:8080/kafka/produce?message=This is my message"> http://localhost:8080/kafka/produce?message=This is my message </a>
 
# consumer end-point

http://localhost:8080/kafka/messages

# Start Zoo Keeper first :

zookeeper-server-start /usr/local/etc/kafka/zookeeper.properties

# Start Kafka Server : 

kafka-server-start /usr/local/etc/kafka/server.properties

During server start,if connection broken issue comes 

To fix this issue, we need to change the server.properties file.

vim /usr/local/etc/kafka/server.properties


Here uncomment the server settings and update the value from
listeners=PLAINTEXT://:9092
to

listeners=PLAINTEXT://localhost:9092

and restart the server and it will work great.


# Create Kafka Topic:

kafka-topics --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 --topic MyTopic


# Initialize Producer console:

kafka-console-producer --broker-list localhost:9092 --topic MyTopic


# Initialize Consumer console:

kafka-console-consumer --bootstrap-server localhost:9092 --topic MyTopic --from-beginning