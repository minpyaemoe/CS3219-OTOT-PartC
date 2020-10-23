# CS3219-OTOT-Task-D (Pub-sub messaging with Kafka Cluster)

## Instructions on how to run

1. Add `0.0.0.0 kfk-1 kfk-2 kfk-3` hosts to the /etc/hosts file as follows:

![alt text](https://github.com/minpyaemoe/CS3219-OTOT-Task-D/blob/main/images/0.PNG)

2. Run `sudo apt-get install kafkacat` to install kafkacat.
3. Run `sudo docker-compose up -d` at root (cloned) folder.
4. Run `sudo docker ps --all` to check all the six containers are up and running.
5. Run `sudo kafkacat -L -b kfk-1:20092` or `sudo kafkacat -L -b kfk-2:30092` or `sudo kafkacat -L -b kfk-3:40092` to identify the controller.
6. Open another terminal and set the controller as a producer e.g. `sudo kafkacat -P -b kfk-1:20092 -t new_topic`.
7. Open another terminal and set another cluster as a consumer e.g. `sudo kafkacat -C -b kfk-2:30092 -t new_topic`.
8. Input some messages at the producer terminal to ensure that they are reflected at the consumer terminal.
9. Open another terminal and stop the controller container using docker command e.g. `sudo docker stop cs3219-otot-task-d_kfk-1_1`.
10. Run `sudo kafkacat -L -b kfk-1:20092` or `sudo kafkacat -L -b kfk-2:30092` or `sudo kafkacat -L -b kfk-3:40092` to observe that another cluster has been appointed as the controller.
11. Input some messages at the producer terminal again to observe that pub-sub messaging system is still running.
