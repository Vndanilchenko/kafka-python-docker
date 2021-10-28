In this project we will explore how to use kafka and python. 

In our example we will parse a culinary site and use its information in transfer between kafka topics with some transformations. We will do all consumers, producers and transformation using python.     

To run all services together we I will use ["cp-all-in-one by Confluent"](https://github.com/confluentinc/cp-all-in-one)




* [first, we will clone kafka and services repo and build images](#sec1) 
* [then install kafka tools to control our kafka-cluster](#sec2)
* [finally, we will create all necessary python code and work with kafka](#sec3)


<a name="sec1"/>

### first, we will clone kafka and services repo and build images

first, let's install docker-compose

<xml/>

    sudo apt-get install docker-compose

![docker compose](images/1.png)

The easiest way to run all services we need is ["cp-all-in-one by Confluent"](https://github.com/confluentinc/cp-all-in-one), let's clone it

<xml/>

    git clone https://github.com/confluentinc/cp-all-in-one

![git clone](images/2.png)

start all services

<xml/>

    sudo docker-compose up -d

![ls](images/3.png)

![compose up](images/4.png)
..
![compose up finish](images/5.png)

check running containers

<xml/>

    sudo docker-compose ps

![compose check](images/6.png)


<a name="sec2"/>

### then install Kafka Tools to control our kafka-cluster

download kafka Tool

<xml/>

    wget https://www.kafkatool.com/download2/offsetexplorer.sh

![kafka tool download](images/7.png)

install Java developer utilities

<xml/>

    sudo apt install openjdk-8-jre

![jdk](images/8.png)

install Kafka Tool

<xml/>

    chmod +x offsetexplorer.sh
    sudo ./offsetexplorer.sh


![install kafka tool](images/9.png)


<a name="sec3"/>

### finally, we will create all necessary python code and work with kafka

##### all code is in ["kafka-python.ipynb"](kafka-python.ipynb), below I will show some screenshots

create producer and send 2 messages

![producer](images/10.png)

check our messages in Kafka Tool

![check messages](images/11.png)

start consumer which will listen to the test_topic and print values from received messages

![consumer](images/12.png)

we will parse a website with recipes, pick up salad recipes, add html to a kafka topic, convert it to json format and transfer it to another topic (json_recipes), the next consumer will pick up information about calorie content, a list of ingredients and cooking time, it will also issue an alert if calories above the threshold

![parse first](images/13.png)

![parse second](images/14.png)

![parse third](images/15.png)

![parse fourth](images/16.png)

![parse fifth](images/17.png)

![parse sixth](images/18.png)

![parse seventh](images/19.png)