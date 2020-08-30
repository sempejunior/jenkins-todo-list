This project is related to study and create pipelines on jenkins local.

###  1. Install Jenkins on Ubuntu

**Add the key to repository**

```
wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
```

**Add the address** 

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

**1-** Click in New Item  
**2-** Put the name of your job and choice the Freestyle project  
**3-** In the Source Code Management select git and put the ssh's   repository and select the key you created before.  
**4-** In the trigger builds select Pool SCM and put * * * *  
**5-** Select Delete workspace before build starts  

### 5. Installation dependencies

Install in your local machine the dependencies and start the server.  

**a) Install pip3**  
```
sudo apt-get update
sudo apt-get -y install python3-pip
```

**b) Install venv**

```sudo pip3 install virtualenv nose coverage nosexcover pylint```

**c) Create and ativate venv (dev)**  

```
cd ../    
virtualenv  --always-copy  venv-django-todolist
source venv-django-todolist/bin/activate
pip install -r requirements.txt
```

**d) Initial data migration**
```
python manage.py makemigrations
python manage.py migrate
```
**e) Create the superuser to acess the platform**  

```python manage.py createsuperuser```

**f) You neeed to do the same for prd .env**  
First you have to change the .env. For you prd enviroment, put this bellow:  

```
# Secret configuration
SECRET_KEY = 'r*5ltfzw-61ksdm41fuul8+hxs$86yo9%k1%k=(!@=-wv4qtyv'
# conf
DEBUG=True

# Database
DB_NAME = "todo"
DB_USER = "devops"
DB_PASSWORD = "mestre"
DB_HOST = "localhost"
DB_PORT = "3306"

```
After the change the .env, execute again steps **d** and **e**.  

**g)Execute the server**  
```python manage.py runserver 0:8000```

### 6. Expose Deamon
This step is related to use docker and containers with jenkins. The first step is to configure and expose daemon docker to external. Follow the steps bellow:

**Create diretory**

```sudo mkdir -p /etc/systemd/system/docker.service.d/```

**Create the file**

```sudo vi /etc/systemd/system/docker.service.d/override.conf```

**Put the text bellow in the file to expose in the port 2376**

```
Service]
ExecStart=
ExecStart=/usr/bin/dockerd -H fd:// -H tcp://0.0.0.0:2376
```
**Reload and Restart Daemon**

```
sudo systemctl daemon-reload
sudo systemctl restart docker.service
```

