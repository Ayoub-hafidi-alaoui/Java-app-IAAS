# Java-app-IAAS
we will try to deploy this project https://github.com/Ayoub-hafidi-alaoui/java-app-devops as IAAS in AWS.

The architecture:

![image](https://github.com/Ayoub-hafidi-alaoui/Java-app-IAAS/assets/55900369/533e234f-3c42-4368-a17d-1e025075330f)

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
# MYSQL
  create EC2 instance but pay attention on two things.
  ## To add key-pair:
  ![image](https://github.com/Ayoub-hafidi-alaoui/Java-app-IAAS/assets/55900369/963671c6-b12b-44de-9cbf-bbe1a1fc1b05)
  ## To add security group
  ![image](https://github.com/Ayoub-hafidi-alaoui/Java-app-IAAS/assets/55900369/cac08a6d-64ee-4f08-9af9-0d54b2fcfe2b)
  and to add script to install mysql in the advanced settings:
  ![image](https://github.com/Ayoub-hafidi-alaoui/Java-app-IAAS/assets/55900369/5c3c9115-56e5-4138-8972-dc30c3efb855)
  You will find the sql script attached in the repo.
  
  ![image](https://github.com/Ayoub-hafidi-alaoui/Java-app-IAAS/assets/55900369/66d8cc9e-a13a-4947-8c6f-ca76f0bbb34c)

# Memcache
  Create EC2 instance you can follow the same steps but you need to change the script that you will find attached in the repo.
  ![image](https://github.com/Ayoub-hafidi-alaoui/Java-app-IAAS/assets/55900369/0f9e4067-583c-4ae0-bb1a-50c1b14abd9c)
# Rabbitmq
 EC2 instance with api key and security group and script in the adveanced settings.
 ![image](https://github.com/Ayoub-hafidi-alaoui/Java-app-IAAS/assets/55900369/b7d941ae-e938-40b7-b3eb-30ce542d0326)

# Web app
  EC2 instance for web app. (pat attention to choose app-SG instead of backend-SG).



# Routing
  We will create a service Route 53
  ![image](https://github.com/Ayoub-hafidi-alaoui/Java-app-IAAS/assets/55900369/cf61a332-da3b-4e23-8d36-4c262265685b)
  go to creat hosted zone:
    choose private hosted zone.
    ![image](https://github.com/Ayoub-hafidi-alaoui/Java-app-IAAS/assets/55900369/696b3148-caea-4362-9bdc-e757a69962a3)
    and choose the closest region to you.
    ![image](https://github.com/Ayoub-hafidi-alaoui/Java-app-IAAS/assets/55900369/94101c08-1de2-4a97-bef4-236f84421939)

  After creation you will find two records:
  ![image](https://github.com/Ayoub-hafidi-alaoui/Java-app-IAAS/assets/55900369/d0c209d7-754a-40fe-8e83-c258f724fcba)

  Go to create new record and create a new record with name rm01 and choose the private ip that you have on your ec2 settings of rm01
  ![image](https://github.com/Ayoub-hafidi-alaoui/Java-app-IAAS/assets/55900369/eeb860bc-66bc-4d31-9478-0e1d0adc2368)

  ![image](https://github.com/Ayoub-hafidi-alaoui/Java-app-IAAS/assets/55900369/1d171edb-156c-4537-9a20-68538e7cd412)
  
  and do the same thing for db01
  
  ![image](https://github.com/Ayoub-hafidi-alaoui/Java-app-IAAS/assets/55900369/76ec0e64-d84a-4adb-a3ee-a3cd29148a57)

  and for mc01

  ![image](https://github.com/Ayoub-hafidi-alaoui/Java-app-IAAS/assets/55900369/d74ac071-6c1b-4fb2-a4b3-346ea6db2212)

  

  You can go right now to the web-app and open a ssh connection and edit the application.properties file:
  ![image](https://github.com/Ayoub-hafidi-alaoui/Java-app-IAAS/assets/55900369/3fd919f6-df35-4c6f-b836-ee96a02d8377)

  ![image](https://github.com/Ayoub-hafidi-alaoui/Java-app-IAAS/assets/55900369/ecce4930-6642-4107-bc45-1463c8b119d4)

  We will need to create a record for app01 in order to route the traffic from the load balancer to the app

  ![image](https://github.com/Ayoub-hafidi-alaoui/Java-app-IAAS/assets/55900369/93b5ffd0-89d9-450b-9745-b91e3bab0774)


  We will return to the creation of EC2 instance of elb:

  # TODO


  You can go to the app:
  run mvn install 
  ![image](https://github.com/Ayoub-hafidi-alaoui/Java-app-IAAS/assets/55900369/c7e2d781-a7a1-4d68-b006-10d6fe912db9)

  delete ROOT folder and copy the war file generated to the ROOT.war 
  ![image](https://github.com/Ayoub-hafidi-alaoui/Java-app-IAAS/assets/55900369/5e7ae1e7-7441-4c96-8743-d5bb677c502f)

  Don't forget to change the owner of the directory /usr/local/tomcat/webapps/ROOT/ to tomcat and group tomcat.
  sudo chown tomcat:tomcat /usr/local/tomcat/webapps/ROOT/
  sudo chown tomcat:tomcat /usr/local/tomcat/webapps/ROOT.war

  I have faced an issue related to java 11. You need to change the version in the web app from 17 to 11.

  If you follow all these steps you can see you web app deployed:
  
  ![image](https://github.com/Ayoub-hafidi-alaoui/Java-app-IAAS/assets/55900369/1215d5d1-643e-4f5f-82b5-69efa6886edc)


  using admin_vp/admin_vp as credentials:

  ![image](https://github.com/Ayoub-hafidi-alaoui/Java-app-IAAS/assets/55900369/e264ee41-66ff-4d93-88b8-878f0e1d915a)

  Data inserted into the cache:

  ![image](https://github.com/Ayoub-hafidi-alaoui/Java-app-IAAS/assets/55900369/b5a03a28-4d52-4e69-9052-c56b5c827962)




  




  
  






    



 
  


  



  


