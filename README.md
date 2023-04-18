# spring-cloud-data-flow
Spring Cloud Data Flow Example with Kafka-binder 

![alt text](https://github.com/ismailraju/spring-cloud-data-flow-example/blob/2e660da5dbcb36a25e0439b6df49a0573ebf0730/image_2023_04_18T09_35_31_122Z.png)

###### Follow Below Steps

###### 1) Apache-Kafka Binary Distribution [Download](http://apachemirror.wuchna.com/kafka/2.3.1/kafka_2.11-2.3.1.tgz).

###### 2) Strat Zookeeper server
> zookeeper-server-start.bat D:\software\kafka_2.11-2.3.1\config\zookeeper.properties

###### 3) Strat Kafka server 
> kafka-server-start.bat D:\software\kafka_2.11-2.3.1\config\server.properties



###### 4) Download Spring Cloud Data Flow Server jar [Download](https://repo.maven.apache.org/maven2/org/springframework/cloud/spring-cloud-dataflow-server/2.10.2/spring-cloud-dataflow-server-2.10.2.jar).

###### 5) Strat Spring Cloud Data Flow Server (http://localhost:9393/dashboard/index.html)
 
> java -jar spring-cloud-dataflow-server-2.10.2.jar



###### 5.1) Download Spring Cloud Data Flow skipper jar [Download](https://repo.maven.apache.org/maven2/org/springframework/cloud/spring-cloud-dataflow-shell/2.10.2/spring-cloud-dataflow-shell-2.10.2.jar).

###### 5.2) Strat Spring Cloud Data Flow skipper( http://localhost:7577/api )
 
> java -jar spring-cloud-skipper-server-2.9.2.jar





###### 6) Download Spring Cloud Data Flow Shell jar [Download](https://repo.maven.apache.org/maven2/org/springframework/cloud/spring-cloud-dataflow-shell/2.10.2/spring-cloud-dataflow-shell-2.10.2.jar).

###### 7) Strat Spring Cloud Data Flow shell 
 
> java -jar spring-cloud-dataflow-shell-2.10.2.jar



###### 8) Register all 3 microservices to Spring Cloud Data Flow Server using below commands

> app register --name product-service --type source --uri file:///D:/.m2/repository/com/javatechie/product-service/0.0.1-SNAPSHOT/product-service-0.0.1-SNAPSHOT.jar

> app register --name discount-service --type processor --uri file:///D:/.m2/repository/com/javatechie/discount-service/0.0.1-SNAPSHOT/discount-service-0.0.1-SNAPSHOT.jar

> app register --name courier-service --type sink --uri file:///D:/.m2/repository/com/javatechie/courier-service/0.0.1-SNAPSHOT/courier-service-0.0.1-SNAPSHOT.jar


[//]: # (> app register --name product-service --type source --uri maven://com.javatechie:product-service:jar:0.0.1-SNAPSHOT)

[//]: # ()
[//]: # (> app register --name discount-service --type processor --uri maven://com.javatechie:discount-service:jar:0.0.1-SNAPSHOT)

[//]: # ()
[//]: # (> app register --name courier-service --type sink --uri maven://com.javatechie:courier-service:jar:0.0.1-SNAPSHOT)


###### 9) Create Cloud Stream to connect between all microservices registered in spring cloud data flow server
> create --name log-data --definition 'product-service | discount-service | courier-service'

###### 10) Strat & Deploy Stream 
> stream deploy --name log-data


#### extra:
```


wget https://repo.maven.apache.org/maven2/org/springframework/cloud/spring-cloud-dataflow-server/2.10.2/spring-cloud-dataflow-server-2.10.2.jar

wget https://repo.maven.apache.org/maven2/org/springframework/cloud/spring-cloud-dataflow-shell/2.10.2/spring-cloud-dataflow-shell-2.10.2.jar
wget https://repo.maven.apache.org/maven2/org/springframework/cloud/spring-cloud-skipper-server/2.9.2/spring-cloud-skipper-server-2.9.2.jar


java -jar spring-cloud-dataflow-server-2.10.2.jar
java -jar spring-cloud-skipper-server-2.9.2.jar
java -jar spring-cloud-dataflow-shell-2.10.2.jar



app register --name product-service --type source --uri maven://com.javatechie:product-service:jar:0.0.1-SNAPSHOT

app register --name discount-service --type processor --uri maven://com.javatechie:discount-service:jar:0.0.1-SNAPSHOT

app register --name courier-service --type sink --uri maven://com.javatechie:courier-service:jar:0.0.1-SNAPSHOT
 


app register --name product-service --type source --uri file:///D:/.m2/repository/com/javatechie/product-service/0.0.1-SNAPSHOT/product-service-0.0.1-SNAPSHOT.jar

app register --name discount-service --type processor --uri file:///D:/.m2/repository/com/javatechie/discount-service/0.0.1-SNAPSHOT/discount-service-0.0.1-SNAPSHOT.jar

app register --name courier-service --type sink --uri file:///D:/.m2/repository/com/javatechie/courier-service/0.0.1-SNAPSHOT/courier-service-0.0.1-SNAPSHOT.jar


```



