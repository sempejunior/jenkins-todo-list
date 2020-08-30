This project is related to study and create pipelines on jenkins local.

1- Install Jenkins on Ubuntu

```wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -```

```sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'```

```sudo apt update```

```sudo apt install jenkins```





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
