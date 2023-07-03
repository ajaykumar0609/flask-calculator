Project Description

The project aims to deploy a web application using Docker Swarm, a container orchestration tool that allows for easy management and scaling of containerized applications. The project will utilize Docker Swarm's production-ready features such as load balancing, rolling updates, and service discovery to ensure high availability and reliability of the web application. The project will involve creating a Dockerfile to package the application into a container and then deploying it onto a Swarm cluster. The Swarm cluster will be configured to provide automated failover, load balancing, and horizontal scaling to the application. The goal of the project is to demonstrate the benefits of Docker Swarm for deploying and managing containerized applications in production environments.

What is Docker Swarm?

Docker Swarm is an orchestration management tool that runs on Docker applications. It helps end-users in creating and deploying a cluster of Docker nodes.

Step1:Take three EC2 instance to make one as Master Node(Leader) and other two as a worker node

Open port 2377 is for connections :

This port is used for communication between the nodes of a Docker Swarm or cluster.

Step2:Install docker on all the nodes with below script

#!/bin/bash
    sudo apt-get update
    sudo apt-get install docker.io -y
    sudo usermod -aG docker $USER
    sudo systemctl start docker
    sudo systemctl enable docker

Master node

docker swarm init so that it will treat this as leader

Step3:Now,move to worker node and issue this command to join these worker nodes with Master one.

issue docker swarm join command over worker nodes which gets generated after docker swarm init over master node.

Worker node-1

Worker Node-2

Step4:Verify the nodes status--docker node ls

Code Availability:https://github.com/gsbarure/flask-calculator.git

Step5:Create a service

specify which container image to use and which commands to execute inside running containers. In the replicated services model, the swarm manager distributes a specific number of replica tasks among the nodes based upon the scale you set in the desired state.

sudo docker service create --name flask-calculator3 --replicas 3 --publish 3000:3000 gajananbarure/gajananb-mycalci-app(Image available on dockerhub--gajananbarure)

Check running container status--docker ps

To check services--docker service ls

open port 3000

Step6:Flask calculator app is successfull on both Manager/worker nodes..!!

you can try some calculations like below:

![image](https://github.com/gsbarure/flask-calculator/assets/125451289/496e0360-d77e-4f09-97f9-821038fda9ac)


Master node:

![image](https://github.com/gsbarure/flask-calculator/assets/125451289/ff6dbfbd-ef4e-4a9c-9fd8-6fb5f0e13d48)


Worker node:

![image](https://github.com/gsbarure/flask-calculator/assets/125451289/6f870afa-2ea0-4658-893d-15c60664f65f)

Application is working as expected,

Tried multiplication with this app!

![image](https://github.com/gsbarure/flask-calculator/assets/125451289/77fb8603-11d9-44ec-a12b-68d816132b6c)


Step7:Auto healing:

Manager manages autohealing if crash/kill something manager will manage the replicas as if killled/crashed it will autocreate

Step8:You can check docker info for more details like also it will show if server is Manager/worker node like below attached snap.

Master Node:

Worker node:

Dockehub image:gajananbarure/gajananb-mycalci-app

Which platform should you use?

Docker swarm vs Kubernetes:

Both Kubernetes and Docker Swarm serve their particular use cases. Which one is best for you depends on your or your organization's current needs.

When starting, Docker Swarm is an easy-to-use solution to manage your containers at scale. If you or your company does not need to manage complex workloads, then Docker Swarm is the right choice.

If your applications are critical and you are looking to include monitoring, security features, high availability, and flexibility, then Kubernetes is the right choice.


Code Availability:https://github.com/gsbarure/flask-calculator.git

Linkdin:https://www.linkedin.com/in/gajanan-barure-7351a4140

***Happy Learning :)***✌✌

Keep learning,Keep growing🎇🎇

#day83#90daysofdevops#devopscommunity#

