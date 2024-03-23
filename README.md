# Java-app-IAAS
This a  java app deployed as IAAS in AWS.
# Create a key pair:
  ![image](https://github.com/Ayoub-hafidi-alaoui/Java-app-IAAS/assets/55900369/f8dd963c-c757-4e05-bc3f-082c0a7e5fe9)
  
  ## Create three security groups:
  First security group between the user and load balancer (allow ssh nad http).
  ![image](https://github.com/Ayoub-hafidi-alaoui/Java-app-IAAS/assets/55900369/3708edb2-c0b3-4895-b67f-38cecde0cda9)
  ## Second security group between load balancer (Nginx) and web app (Java app + tomcat)
  ![image](https://github.com/Ayoub-hafidi-alaoui/Java-app-IAAS/assets/55900369/e3309acc-7e5f-462d-960d-7ea491b6204f)
  ## third security group betweeen web app and rabbitmq memcache and mysql.
 ![image](https://github.com/Ayoub-hafidi-alaoui/Java-app-IAAS/assets/55900369/f538e562-4566-4189-971a-fb83168d21f8)


# Create EC2 instances:
  create EC2 instance but pay attention on two things.
  ## To add key-pair:
  ![image](https://github.com/Ayoub-hafidi-alaoui/Java-app-IAAS/assets/55900369/963671c6-b12b-44de-9cbf-bbe1a1fc1b05)
  ## To add security group
  ![image](https://github.com/Ayoub-hafidi-alaoui/Java-app-IAAS/assets/55900369/cac08a6d-64ee-4f08-9af9-0d54b2fcfe2b)
  and to add script to install mysql in the advanced settings:
  ![image](https://github.com/Ayoub-hafidi-alaoui/Java-app-IAAS/assets/55900369/5c3c9115-56e5-4138-8972-dc30c3efb855)
  You will find the sql script attached in the repo.
  
  ![image](https://github.com/Ayoub-hafidi-alaoui/Java-app-IAAS/assets/55900369/66d8cc9e-a13a-4947-8c6f-ca76f0bbb34c)
  

  



  


