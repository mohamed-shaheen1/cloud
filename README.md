# cloud assingment to setup instructions

## Overreview of the assignment
-This project implements a simplified backend system for an e-commerce platform using AWS services in an event-driven architecture. When a new order is placed, it is processed through a system of notifications, queues, and serverless functions, and is reliably stored in a NoSQL database.
## First setting up dynamoDB
- using amazon cli navigate to DynamoDB
- c reate table 
- name the table Orders
- and set partion key = orderId
![Alt text](dynamo.png)
  ## second setup the Queue
  - navigate to sqs
  - first create a queue and name DLQ QUEUE this will be used to clear the primary queue
  - then I created a second Queue named OrderQueue using standerd settings and a visiability timout of 30 seconds
  - add the DLQ queue to the OrderQueue
  - sqs screenshot with messages 
![Alt text](sqs.png).
## third step sns setup
- create a topic named OrderTopic
- add the OrderQueue as a subscription
- ![Alt text](topic.png).
![Alt text](subscription.png).
## creating lambda function
- create function
- give it a name mine is orderFunction
- choose runtime node.js 22.x
- defualt permmsions then deploy
- after that we go to configuration > perrmissions > excution role > add perrmission > attach Policy > give sqs and dynamo db full access

![Alt text](image.png).

- deploy the code on lambda function
- add sqs trigger and choose OrderQueue

## database after the test 

![Alt text](database.png).









