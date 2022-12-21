# Getting Started Custome Jenkins

Required for installation:
* Docker
* Docker-compose
* Make

## Setting up Jenkins

1. Clone project from github
    ```git clone https://github.com/nnstu-appmath/infra.git```
2. Go to the project repository
    ```cd infra/jenkins```
3.  Up docker-compose
   ```make up```
4. Use
   ```docker ps```
   for check running containers.
5. Check url from browser http://localhost:8080
6. Use this command
    ```docker logs <my_jenkins>```
    or this command
    ```docker exec <my_jenkins> cat /var/jenkins_home/secretsinitialAdminPassword```
    to get the password for unlock Jenkins.
7.  Install suggested plugins
   ![](https://fixmypc.ru/media/uploads/2022/02/09/6.jpg)
8. Create User.
9. Install Docker plugin and Docker pipeline plugin:
   Manage Jenkins -> Manage Plugins -> Available plugins -> Search Docker and choose Docker plugin and Docker pipeline -> Install without restart.


Сongratulations, you was deployed the Jenkins container with docker and docker-compose for the next job!

## Makefile commands

If you want to restart jenkins container:
   ```make init```
If stop:
   ```make down```
If start:
   ```make up```

## How to create a job to deploy LMNAD project 

1. New Item 
2. Enter an item name
3. Choose Pipeline 
4. Scroll down to Pipeline -> choose Pipeline script from SCM 
5. SCM choose Git 
6. Put the Repository URL 
   ```https://github.com/nnstu-appmath/lmnad.git``` 
   and credentials (if you need to connect with SSH 
   ```git@github.com:nnstu-appmath/lmnad.git```)
7. Branches to Build -> Branch Specifies 
   ```*/jenkins``` 
8. Additional Behaviours -> Add -> Clean before checkout -> Mark Delete untracted nested repositories
9.  Script Path ```Jenkinsfile```
10. Save

Now you can build your job!
