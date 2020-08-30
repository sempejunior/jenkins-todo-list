This project is related to study and create pipelines on jenkins local.

###  1- Install Jenkins on Ubuntu

```wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'```
sudo apt update
sudo apt install jenkins```

### 2- Install MySql

You can also use one docker image with mySql or you can install mySql in you machine. The steps below are for local installation.

```sudo apt-get update```
```sudo apt-get install mysql-server```

Start mySql
```sudo systemctl start mysql```

Create users
```CREATE USER 'devops'@'localhost' IDENTIFIED BY 'mestre';```
```CREATE USER 'devops_dev'@'localhost' IDENTIFIED BY 'mestre';```

Grant for users
```GRANT ALL PRIVILEGES ON * . * TO 'devops'@'localhost';```
```GRANT ALL PRIVILEGES ON * . * TO 'devops_dev'@'localhost';```
```FLUSH PRIVILEGES;```

Create database
```CREATE DATABASE todo;```
```CREATE DATABASE todo;```

### Installation

Install the dependencies and start the server.

```sh
$ cd django-todolist
$ pip install -r requirements.txt
$ python manage.py migrate # Running the migrations
$ python manage.py createsuperuser # Create a superuser
$ python manage.py runserver
```




License
----

GPL
