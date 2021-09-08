# Docker-documentation

#### To create a web server:
```
$ cd /path/to/python-docker
$ pip3 install Flask
$ pip3 freeze > requirements.txt
$ touch app.py
```

#### I added the following code into the app.py file.
```
from flask import Flask
app = Flask(__name__)

@app.route('/')
def firstdocker():
    return 'Welcome, This is my first Dockerfile'
```
#### Test the application:
```
$ python3 -m flask run 
```
#### Create a Dockerfile for Python
```

FROM python:3.8-slim-buster

WORKDIR /app

COPY requirements.txt requirements.txt
RUN pip3 install -r requirements.txt

COPY . .

CMD [ "python3", "-m" , "flask", "run", "--host=0.0.0.0"]
```
#### Build docker image: 
```
$ docker build --tag first-docker .
```

#### View local images 
```
docker images
```

#### Run image as a container with a publish tag and a default port
 ```
 $ docker run --publish 5000:5000 first-docker
 ```
 
 ##### Run the `curl` command in a new terminal. 
 ```
 $ curl localhost:5000
 ```
 #### Voila!
 ```
 $ curl localhost:5000
Welcome, This is my first Dockerfile
```


##### Run in detached mode: 
```
docker run -d -p 5000:5000 first-docker
```

#### To display a list of containers running on the machine.
run the `docker ps` command.
``$ docker stop`` Stops a container.



#### I updated Dockerfile from:
 ```
Welcome, This is my first Dockerfile
 ```
to: 
```
Docker is awesome!
```
in the `app.py` file.


#### build updated version of the image:
```
docker build -t first-docker .
```
Start a new container using the updated code: 
```
docker run -dp 5000:5000 first-docker
```
throws an error?!

#### Remove the old container.
container ID `docker ps`.

`$ docker stop <the-container-id>` stops the container.

remove container `$ docker rm <the-container-id>`.

