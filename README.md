 *** setup kafka in windows machine ***

Step 1: Install Java

set JAVA HOME and PATH variable

Step 2: Download and Extract Kafka

Go to the Apache Kafka website (https://kafka.apache.org/downloads) and download the latest stable release of Kafka Extract the downloaded archive to a directory of your choice, e.g., C:\kafka.

Step 3: Configure Kafka Open the config directory within the extracted Kafka folder (C:\kafka\config).

a): Configure the following properties in the server.properties file: 
	listeners PLAINTEXT://localhost:9092
	log.dirs=C:/kafka/logs

b): Configure the following properties in the zookeeper.properties file:
	dataDir=C:/kafka/zookeeper-tmp-data

Step 4: Using below command Test kafka setup

a): start kafka servers
C:\kafka>bin\windows\zookeeper-server-start.bat config\zookeeper.properties
C:\kafka>bin\windows\kafka-server-start.bat config\server.properties

b): create new topic
C:\kafka>bin\windows\kafka-topics.bat --create--topic quickstrt-event--bootstrap-server localhost:9092
C:\kafka>bin\windows\kafka-topics.bat --describe --topic quickstrt-event--bootstrap-server localhost:9092

d): consume message from kafka topic
C:\kafka>bin\windows\kafka-console-consumer.bat --topic quickstrt-event--from-beginning --bootstrap-server locahost:9092
