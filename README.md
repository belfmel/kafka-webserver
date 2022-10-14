# Web Server Using Kafka

This project involves creating a web server using Kafka.
- I used a Docker image created by Confluent that installs all of the necessary Kafka components including, the broker and ZooKeeper.
- I created a Python application that publishes vehicle location longitude-latitude data to a Kafka topic (NodeJSConsumer/PublishVehicleCoordinates.py).  This is to simulate an IoT device that publishes the latitude and longitude coordinates of vehicles locations to Kafka.
- I used Node.js to start a web server that acts as a consumer for the messages received from the Kafka application

#### Steps used to run application

1. Navigate to kafka-docker and run ```docker-compose up``` to start up 9 different docker containers
2. Navigate to the following url ```http://localhost:9021```. This is the Confluent Control Center, and it allows you to check the status of the Kafka cluster that you spun up
3. Create a new Kafka topic called ```vehicle-coordinates``` and set the number of partitions to 1.  Select ```Create with default settings```
4. Run python script ```python3 NodeJSConsumer/PublishVehicleCoordinates.py``` to publish coordinates to Kafka topic ```vehicle-coordinates``` - You can see the published coordinates on the Confluent Control Central
5. Install package ```npm install node-rdkafka``` and then start up node web server using command ```node NodeJSConsumer/server.js```
6. Navigate to web page ```http://localhost:5002``` 
7. Click on the button ```Consume Vehicle Coordinates``` to verify that the data is being consumed and there are no errors

#### Technologies and Libraries used:
- Kafka
- Node.js
- Express
- node-rdkafka
