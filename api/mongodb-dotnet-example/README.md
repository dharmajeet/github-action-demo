![MongoDB and C# logo](./images/banner.png)

## Introduction

## Prerequisite 
1. Docker for desktop should be installed
2. VS code or Other IDE should be installed

## Getting Started

1. Open Terminal window in VS code 
2. Go to mongodb-dotnet-example directory
3. Run following command 
	a. docker build -t mongodb-dotnet-example:0.1.0 . 
	  or 
	  docker build -t mongodb-dotnet-example:0.1.dev . --build-arg ENVIRONMENT=Development --build-arg LOG_LEVEL=Debug
	  
	b. docker create -p 8080:80 -e ASPNETCORE_ENVIRONMENT=Development -e Logging__Loglevel__Default=Debug  -e Logging__Loglevel__Microsoft.AspNetCore=Debug --name mongodb-dotnet-example mongodb-dotnet-example
	c. docker start  mongodb-dotnet-example
	d. docker logs mongodb-dotnet-example
	e. Open http://localhost:8080/swagger/index.html in browser


4. Setup MongoDB on docker
	a. docker pull mongo
	b. docker pull mongo-express
	c. docker network ls
	d. docker network create mongo-network
	e. docker run -d -p 27017:27017 -e MONGO_INITDB_ROOT_USERNAME=admin -e MONGO_INITDB_ROOT_PASSWORD=password --name mongo --net mongo-network mongo
	f. Now you may able to connect with db instance with connection:  mongodb://localhost:27017 : user name : amdin and Password: P@ssw0rd
	g. docker run -d -p 8081:8081 -e ME_CONFIG_MONGODB_URL="mongodb://admin:password@mongo/?authMechanism=DEFAULT" --name mongo-express --net mongo-network mongo-express


## Note
If the docker for desktop is running on windows machine and container running on wsl
To see the volumne location. need to find on following path
\\wsl$\docker-desktop-data\version-pack-data\community\docker\volumes
or
\\wsl$\docker-desktop-data\data\docker\volumes

To see the volumn mapping run following command
docker inspect <container name>



 