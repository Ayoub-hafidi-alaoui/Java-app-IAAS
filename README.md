# Java-app-IAAS
This a  java app deployed as IAAS in AWS.
Create a key pair:
![image](https://github.com/Ayoub-hafidi-alaoui/Java-app-IAAS/assets/55900369/f8dd963c-c757-4e05-bc3f-082c0a7e5fe9)

Create three security groups:
First security group between the user and load balancer (allow ssh nad http).
![image](https://github.com/Ayoub-hafidi-alaoui/Java-app-IAAS/assets/55900369/3708edb2-c0b3-4895-b67f-38cecde0cda9)
Second security group between load balancer (Nginx) and web app (Java app + tomcat)
![image](https://github.com/Ayoub-hafidi-alaoui/Java-app-IAAS/assets/55900369/e3309acc-7e5f-462d-960d-7ea491b6204f)
third security group betweeen web app and rabbitmq memcache and mysql.
![image](https://github.com/Ayoub-hafidi-alaoui/Java-app-IAAS/assets/55900369/de0187c1-c377-4ed1-afe9-09ce12171f96)
