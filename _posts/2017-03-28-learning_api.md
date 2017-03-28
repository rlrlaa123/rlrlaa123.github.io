---
title: Simple API tutorial
subtitle: Django-RestFramework, AWS-ec2, Poderosa, Git
image: https://strongloop.com/wp-content/uploads/2014/06/SL_Connect_APIServer.png
---

###### Today I learned how to create api server on hosted web on AWS EC2 instance, using Poderosa. She emphasized that linux environment is crucial for development. Also, from now on I should update every code on Git.

With this tutorial, you can build rest api and host it on AWS. From the api server you can receive data from web or mobile applications.

### Sketchy Process
1. Build django-restframework
   * test on localhost
2. EC2 hosting
   * Get _**public key**_
   * Open _**port**_
3. Connect to Server with Poderosa
4. upload files on git
5. get files from server and run

![api example1](/img/api_tutorial1.PNG)
![api example2](/img/api_tutorial2.jpg)
This is the final screen of api in web and application. According to what kind of api I build I can save data on the server and get it from anywhere.

I'll start to follow the sketchy process.

### 1. Build django-restframework
I made simple api using django-framework referenced from __quickstart__ tutorial from django restframework homepage.
http://www.django-rest-framework.org/tutorial/quickstart/
#### Project Setup
```python
# Create the project directory
mkdir tutorial
cd tutorial

# Create a virtualenv to isolate our package dependencies locally
virtualenv env
source env/bin/activate  # On Windows use `env\Scripts\activate`

# Install Django and Django REST framework into the virtualenv
pip install django
pip install djangorestframework

# Set up a new project with a single application
django-admin.py startproject tutorial .  # Note the trailing '.' character
cd tutorial
django-admin.py startapp quickstart
cd ..
```
When starting a new project, it is more convenient to create virtual environment with __virtualenv__. Because usually you download many libraries in different version and it will end up compiled on your computer. That can produce severe version conflict in the future. Next, you download the libraries and create new project and application.
> If you also want to use virtual environment on __Pycharm__ you should simply import the directory in __Pycharm__.

Sync your database
        ```python
        python manage.py migrate
        ```
initialize user named admin with a password of password123. 
        ```python
        python manage.py createsuperuser
        ```
Once you've set up a database and initial user created and ready to go.

From now on, you can copy and paste the code on the django restframework website' __quickstart__.

#### Serializer
Serializer is the setup point on where you choose which and how data will be showed on the api.
#### Views
