# AMQCLI
An ActiveMQ - Full featured JMS Client to  send,receive messages to both Queue and Topic.  Also covers various types of subscription and message processing

# Prerequisite 
Install JDK 
```sh
sudo zypper --non-interactive install java-17-openjdk-devel
```
# Build

build QueueSender file
```sh
 javac -cp ".:activemq-all-5.8.0.jar:javax.jms.jar:slf4j.jar:logback.jar" QueueSender.java
 ```
 build QueueReceiver file
```sh
 javac -cp ".:activemq-all-5.8.0.jar:javax.jms.jar:slf4j.jar:logback.jar" QueueReceiver.java
 ```
 # RUN


One can provide serviceIP for activemq service. Use 61616 port as it doesn't require tls connection
 ```sh
ec2-user@ip-172-31-92-40:~/test/AMQCLI> kubectl get svc -n atlantic | grep activemq
active-mq-activemq-postgres        NodePort    10.43.203.128   <none>        80:31453/TCP,443:30762/TCP,8161:32146/TCP,61714:32167/TCP,5672:30895/TCP,61613:32723/TCP,61616:31669/TCP,1883:32608/TCP   2d
  ```
### Run QueueSender to send message
 ```sh
 java -cp ".:activemq-all-5.8.0.jar:javax.jms.jar:logback.jar:AMQCLI.jar"  QueueSender
  ```
 ##### CLI should promp for queue, username, password and connection url 
 ###
 ```
queue name: test
User: admin
Passoward: <activemq password>
Connection url - tcp://<serviceip>:61616
 ```
### Run QueueReciever to recieve message
 ```sh
 java -cp ".:activemq-all-5.8.0.jar:javax.jms.jar:logback.jar:AMQCLI.jar"  QueueReciever
  ```
 ##### CLI should promp for queue, username, password and connection url 
 ###
 ```
queue name: test
User: admin
Passoward: <activemq password>
Connection url - tcp://<serviceip>:61616
 ```
###### Post entering required information, CLI should print recieved messages 

### Detailed Instruction on how to use this tool with practical examples are avilable here
http://www.middlewareinventory.com/blog/activemq-simple-jms-client-program-to-test-queue-and-topic/

## References
Code - https://github.com/AKSarav/AMQCLI
Example - https://www.middlewareinventory.com/blog/activemq-simple-jms-client-program-to-test-queue-and-topic/#How_to_use_the_Simple_JMS_Client_AMQCLIjar
Downloads: http://archive.apache.org/dist/activemq/apache-activemq/5.8.0/apache-activemq-5.8.0-bin.tar.gz
