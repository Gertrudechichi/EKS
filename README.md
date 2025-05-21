Amazon Elastic Container Service for Kubernetes is a container orchestrating tool used for manging containerised application. A cluster may contain several containerized applications and management of the pods hosting these applications is very tedious. EKS is a container orchestration tool that manages containerized applications in a Kubernetes cluster.With amazon EKS, you have a certain level of control over your containers via the kubernetes API.
 
With Kubectl which is a command line tool which allows you to interact with kubernetes cluster, you can create, update or even delet deployment , pods and services using the command line interface.Kubectl provides a medium for controlling your kubernetes cluster .

In a scenario where you have a workload that requires running containers on multiple EC2 instances which form a cluster, it will be difficult to manage the cluster by monitoring and scaling to meet demands. With kubectl, interaction with the Kubernetes API for automation of  repetitive tasks, such as scaling or updating deployments is made possible.







This lab demonstrates the steps to deploy and manage a containerized Nginx 
application on an Amazon Elastic Container Service for Kubernetes cluster. 


The procedures are highlighted below: 
EKSCTL was installed because it was needed to make API calls to AWS for the provisioning and management of the EKS cluster.



![image alt](https://github.com/Gertrudechichi/EKS/blob/577a8d9c5bf5808749aca11b9fe46ff0527689c4/Screenshot%202025-05-21%20123222.png)

Kubectl was also installed to interact with the Kubernetes control plane in other to manage applications, nodes and pods in the cluster upon provisioning.





![image alt](https://github.com/Gertrudechichi/EKS/blob/577a8d9c5bf5808749aca11b9fe46ff0527689c4/Screenshot%202025-05-21%20123248.png)


The EKS cluster was provisioned with the configurations below using the eksctl command line tool. 




![image alt](https://github.com/Gertrudechichi/EKS/blob/577a8d9c5bf5808749aca11b9fe46ff0527689c4/Screenshot%202025-05-21%20123300.png)







![image alt](https://github.com/Gertrudechichi/EKS/blob/577a8d9c5bf5808749aca11b9fe46ff0527689c4/Screenshot%202025-05-21%20123312.png)


A deployment file and a service file was cloned from a git hub repository as shown below 



![image alt](https://github.com/Gertrudechichi/EKS/blob/577a8d9c5bf5808749aca11b9fe46ff0527689c4/Screenshot%202025-05-21%20123333.png)






![image alt](https://github.com/Gertrudechichi/EKS/blob/577a8d9c5bf5808749aca11b9fe46ff0527689c4/Screenshot%202025-05-21%20123353.png)






![image alt](https://github.com/Gertrudechichi/EKS/blob/577a8d9c5bf5808749aca11b9fe46ff0527689c4/Screenshot%202025-05-21%20123459.png)







![image alt](https://github.com/Gertrudechichi/EKS/blob/577a8d9c5bf5808749aca11b9fe46ff0527689c4/Screenshot%202025-05-21%20123519.png)


After cloning the repository containing the Deployment and Service files, both files were applied to the Kubernetes cluster to ensure that the ngnix application is deployed and running in the cluster and also ensure that the application is exposed to the public internet or internal network through the Service. 



![image alt](https://github.com/Gertrudechichi/EKS/blob/577a8d9c5bf5808749aca11b9fe46ff0527689c4/Screenshot%202025-05-21%20123645.png)


The nodes were ready and the pods were up and running as well. The load balancer was attached to the node as well.


![image alt](https://github.com/Gertrudechichi/EKS/blob/577a8d9c5bf5808749aca11b9fe46ff0527689c4/Screenshot%202025-05-21%20123700.png)

This was verified from the AWS console.

![image alt](https://github.com/Gertrudechichi/EKS/blob/577a8d9c5bf5808749aca11b9fe46ff0527689c4/Screenshot%202025-05-21%20123717.png)




![image alt](https://github.com/Gertrudechichi/EKS/blob/577a8d9c5bf5808749aca11b9fe46ff0527689c4/Screenshot%202025-05-21%20123733.png)





![image alt](https://github.com/Gertrudechichi/EKS/blob/577a8d9c5bf5808749aca11b9fe46ff0527689c4/Screenshot%202025-05-21%20123748.png)


After pasting the DNS of the load balancer on the web browser, this was displayed.

![image alt](https://github.com/Gertrudechichi/EKS/blob/577a8d9c5bf5808749aca11b9fe46ff0527689c4/Screenshot%202025-05-21%20123804.png)


I tested cluster availability by stopping nodes and monitoring the status.  
The screenshot below shows that the node was shutting down .


![image alt](https://github.com/Gertrudechichi/EKS/blob/577a8d9c5bf5808749aca11b9fe46ff0527689c4/Screenshot%202025-05-21%20123817.png)



After sometime it was confirmed that there was no resource available meaning the node was successfully terminated.

![image alt](https://github.com/Gertrudechichi/EKS/blob/577a8d9c5bf5808749aca11b9fe46ff0527689c4/Screenshot%202025-05-21%20123829.png)


After sometime, there was an initiation of the node on the console


![image alt](https://github.com/Gertrudechichi/EKS/blob/577a8d9c5bf5808749aca11b9fe46ff0527689c4/Screenshot%202025-05-21%20123841.png)



And the node was ready after a period as shown below. 


![image alt](https://github.com/Gertrudechichi/EKS/blob/577a8d9c5bf5808749aca11b9fe46ff0527689c4/Screenshot%202025-05-21%20123854.png)

As expected, when nodes  were terminated, Kubernetes detected the loss and automatically provisioned new ones, ensuring high availability and reducing administrative burden.
