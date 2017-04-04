---
title: Simple API tutorial(2)
subtitle: Django-RestFramework, AWS-ec2, Poderosa, Git
image: http://www.commzgate.com/assets/img/commzgate_cloud_api.png
---
###### Will start from __2. EC2 hosting__

### Sketchy Process
1. Build django-restframework
   * test on localhost
2. EC2 hosting
   * Get _**public key**_
   * Open _**port**_
3. Connect to Server with Poderosa
4. Get api files from Git.

### 2. EC2 hosting
Hosting means you are borrowing a certain space from another computer. Server is a computer that should be running 24 hours. People like me cannot run server all day so we borrow the some space from server computers. And Amazon is one of the biggest cloud hosting company in the world. 
AWS is free for one year for first user if you have VISA or MasterCard you can make an account.
1. Go to https://www.aws.amazon.com and start EC2
2. Create new instance with linux and launch it.
   * You will receive a key pair file like this '*filename*__.pem__'
   * You should safely store this in your directory and never loose it.
3. Once you launch the instance, you also need to open *port*
   * *port* is the gateway for certain network services on ip address like world wide web open HTTP, this will allow the ip address to be searched from the web browser.
   * Go to Security group and click *Edit* button in inbound pannel.
   * Click Add Rule
      * Type: Custom TCP Rule
      * Protocol: TCP
      * Prot Range: 8080
      * Source: Anyhwere (So that anyone can approach this server, this will create one more rule) & 0.0.0.0(upper), ::/0(below)
      
Now you finished borrowing and creating instance on the AWS. Next, we'll learn how we enter the remote server from my computer.

### 3. Connect to Server with Poderosa
AWS EC2 server is remote server probably located in USA so our computer need to find a way to work on that server. Usually many people use PuTTY or maybe Xshell, but there's same software with better design and UI, Poderosa.
1. *File>New Telnet/SSH Connection*
2. Fill New Connection
   * Host : Public DNS (from EC2)
   * Protocol: SSH2
   * Port: SSH(22)
   * Account: ec2-user
   * Authentication: Public Key
   * Key File: this is where you put your key pair, _**.pem**_ file you saved.

and this will do the job. You will see something like below picture. It means you are in your server you just hosted from AWS.
![](img/api-tutorial.PNG)

### 4. Get api files from Git.
1. pull files from the server
2. write __**python manage.py runserver o.o.o.o:8080**_
    * It will run server on port 0.0.0.0:8080
3. Check your api from browser 
    * copy and paste the host name with :8080 port number and you will see the result like the one we saw at tutorial 1.
![](img/api-tutorial.PNG)
