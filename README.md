This project is related to study and create pipelines on jenkins local.

###  1. Install Jenkins on Ubuntu

**Add the key to repository**

```
wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
```

**Add the adress** 

```
sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
```

**Execute the update for apt use the new repository**

```sudo apt update```

**Install Jenkins**

```sudo apt install jenkins```

**Start Jenkins**

```sudo systemctl start jenkins```

### 2. Install MySql

You can also use one docker image with mySql or you can install mySql in you machine. The steps below are for local installation.

**Install MySql**

```
sudo apt-get update &nbsp;
sudo apt-get install mysql-server
```

**Start mySql**

```sudo systemctl start mysql```

**Create users**

```
CREATE USER 'devops'@'localhost' IDENTIFIED BY 'mestre';
CREATE USER 'devops_dev'@'localhost' IDENTIFIED BY 'mestre';
```

**Grant for users**

```
GRANT ALL PRIVILEGES ON * . * TO 'devops'@'localhost';
GRANT ALL PRIVILEGES ON * . * TO 'devops_dev'@'localhost';
FLUSH PRIVILEGES;
```

**Create database**

```
CREATE DATABASE todo;
CREATE DATABASE todo;
```

### 3. Put your sh key on jenkins

If you dont have this key, you need to create and after execute the steps below.

**Cat the key**
```cat ~/.ssh/id_rsa```

Put your sh key on your jenkins &nbsp;
Open this windows &nbsp;

**Click in your profile** / **Credentials** / **Jenkins** / **Global Credentials** / **Add Crendentials** / SSH Username with private key [ *put your key* ]


### 4. Create your first job
In your jenkins, execute the steps.

**1-** Click in New Item &nbsp;
**2-** Put the name of your job and choice the Freestyle project &nbsp;
**3-** In the Source Code Management select git and put the ssh's repository and select the key you created before. &nbsp;
**4-** In the trigger builds select Pool SCM and put * * * * &nbsp;
**5-** Select Delete workspace before build starts &nbsp;




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
