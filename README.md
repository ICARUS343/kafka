# <h3>kafka</h3>
Read more about kafka here: https://kafka.apache.org/
To run the kafka producer first download kafka from https://kafka.apache.org/downloads
Unzip and open the kafka directory.
First run zookeeper by ruuning this command: bin/zookeeper-server-start.sh config/zookeeper.properties
<h5>To run multiserver broker: </h5>
1. open config/server.properties
  a. Remove the comment '#' from #listeners=PLAINTEXT://:9092
2. cp config/server.properties config/server-1.properties and make the following changes:
  a. #listeners=PLAINTEXT://:9092 -> #listeners=PLAINTEXT://:9093
  b. broker.id=0 -> broker.id=1
  c. log.dirs=/tmp/kafka-logs -> log.dirs=/tmp/kafka-logs-1
3. cp config/server.properties config/server-1.properties and make the following changes:
  a. #listeners=PLAINTEXT://:9092 -> #listeners=PLAINTEXT://:9094
  b. broker.id=0 -> broker.id=2
  c. log.dirs=/tmp/kafka-logs -> log.dirs=/tmp/kafka-logs-2
 
4. Now run all 3 brokers 
bin/kafka-server-start.sh config/server.properties
bin/kafka-server-start.sh config/server-1.properties
bin/kafka-server-start.sh config/server.properties


Now run the gradel project.
