Dockers Architecture:
   * Docker Server : The Server that runs the Docker Daemon & this Daemon is used to Build,Run,Distribute Containers.
   * Docker Client : 
        * The Interface/Client that interact with Docker Daemon & this client can run on different Machine as well.
        * Basically works like Client/Server Architecture.
	* REST API Communication happens between Docket Client & Docket Server.
        * Docker Registry :- This stores all the Docker Images. 
   * Docker Image is nothing but template that is being used to build the Containers.
        * It is usually a separate Server.
        * Docker Images are stored in same Layer.
        * Two Image can use the same Layer.
        * Eg:- If you have Linux Docker Image & You have installed WordPress on Linux Image, It both share the same Layer.
			 
Practical Session:
  * [apt get install Docker.io] - To install docker on Debian.
  * [yum install docker] ->to install docker on RHEL
  * [docker run hello-world] -> It will create Containers named "Hello-World". It will get the "Hello-World" Image from Docker Hub. 
  * [docker run docker/whalesay cowsay 	boo] -> It will create container with docker whale image sayig Boo.
  * "docker ps" - It will show the running containers.
  * "docker ps -a" - It will show all the containers status either running or stopped.
	* Each Container have Process ID 1, If that process ID exists then the Containers is alive and if not the container is not alive.
	* The PID 1 Process runs inside the Containers and not outside & so the multiple containers can run on PID 1 simultaneously
  * "docker run ubuntu:trusty" -> This will create ubuntu containers.
  * "docker run -i -t ubuntu:trusty" -> This will create Ubuntu Containers and show the interactive output to the terminal/Screen.
  * "docker run -i -t -d ubuntu:trusty" -> This will create and run the containers in back ground.
  * "docker stop <Container ID> -> Used to stop the running Containers.
				(or) 
  * "docker stop <Container Name>
  * "docker run -i -t -d --name MyFirstContainer1 ubuntu:trusty" -> New Containers with name as MyFirstContainer1 is created.
  * "docker attach 	<Container Name>" -> Use this command to enter/switch to running container and only when PID 1 of this container is listening for Input.
  * "docker start <Container name>" -> To Start the Container.
	Exit command will stop the Container since it exits from PID1 Process.
	Question:- How do we run web application and make it run for ever?
	PID1 should be non exiting Process.
	Run the Container with -d flag
  * "docker run <container name> <any Custom comamnd> -> Adding custom command to end of the docker run application will change the Process ID of Container
	from PID1 to other PID
	Eg:- docker run ubuntu:trusty ls -al
 * "docker rm <container name> ->Remove the stopped container from docker Daemon.
 * "docker rm" -> To Remove all the stopped containers from the Daemon.
 * "docker exec -i -t <Container Name> <Command> -> This command is used to enter running container using other PID and exiting out from this container will not close/stop the container running in PID1
Example:-
 * docker exec -i -t docker1 bash it will enter into bash shell on my docker1 container even though another
		bash is running under PID 1 for the same container.
 * "docker logs <container name> -> To View the output of the Container. Used for debugging the containers.
 * "docket logs -f <container name> ->To View the output of container logs similar to Tail -f file name. 
			 We can't restart the application that is running inside container. We have to either stop/start the entire container or spun up another container with new configuration.Basically we can't restart PID1. If we do, the container will be stopped.
 * Port Mapping: Port Mapping has to be done during creation of Container & not after creation of Container.
 * "docker run -d -p 1234:80 ngix" -> This will Map the host port 1234 to Port 80 of Ngix Web Server that listen inside the containers. 
So that we can access ngix Web Server using http://localhost:1234 from outside.
 * "docket run -P ngix" -> It will Map the random port on the host to port that ngix container is listening inside.
 * Volume Mapping: Volume Mapping used to Map the Folder or file from the host machine to inside the container.

 Container Automating Image Build
 * "docker images" -> This will shows the images that are cached in the Docker Daemon.
 * "docker pull" -> Pull image from Repository.
 *  "docker pull ubuntu:trusty" -> This will pull the latest Ubuntu from Central Repository & ignore the one that is already Cached.
 Creating Docker File:
	* create new file named "Dockerfile"   
        * FROM ubuntu:trusty					 ->Specify the base image for this Docker file.
	* MAINTAINER Vivek T					 ->Specify the Name of the creator.
	* Run apt-get update					 ->Specify the command & In this case I want to have apt-get package update to date
	* Run apt-get install -y nano          ->Install the Nano editor.
	* CMD ["ping" ,"locahost"] 		->PID 1 of this Docker Image.
	* 					 ->CMD can go as Entry Point.
	* Example:
		CMD ["localhost"]
		ENTRYPOINT  ["ping"]
                ENTRYPOINT  ["ping" ,"locahost"]	 ->Used not to have anyone override the PID 1.
						
 * "docker build -t myfirstimage"
 * "docker build --rm -ti myfirstimage	-> If you specify the --rm flag Once, the docker stop it will be removed from Docker Daemon.
 * "docker login"
 * "docker tag <Image ID> <Docker HUB ID>/<Image Name>:<Version Name> - To add New tag to existing container with the new Image name.
						Eg:- docker tag a3fdgnanw32 vivekT/MyFirstImage:V1
 * "docker push "<Docker HUB ID>/<Image Name>:<Version Name>" -> To Push Docker image to Docker HUB.
 * "docker pull "<Docker HUB ID>/<Image Name>:<Version Name>" -> To Pull Docker Image from the Docker HUB.
 * Docker Network:-
 * "docker inspect <Container Name> or <Container ID>" -> To get complete details of the given container.
 * "docket inspect  -format "{{.NetworkSettings.Network.bridge.IPAddress}}' <Contianer Name> -> To get particular details of container. like IP
 * "docker network ls" -> To view all the N/W in the Docker. 
			Bridge: Default N/W. All Container by default will be on this N/W.
				Host:- N/w on which the your host machine is running.
					none:-It it used inside by Docker Daemon. It for use by daemon for internal Purpose.
 * "docker run -dti --name <Container Name 1>" --link <Container Name 2> 	ubuntu:trusty" -> Creating link between Container 1 & 2 during creation.	
 * "docker network create <Network Name>" --> To Create Docker Network.
"docker run -dti --name <Container Name 1>" --network <Network Name>  ->Run the docker in different Network.
 "docker network connect nw1 <Container Name 1>" -- this will connect network nw1 to Container 1.
Docker Compose:-
             It is simplest & Basic form Docker orchestration Tool.
			   Create .yml file with all the instruction.
				docker-compose up    ->  Execute the yml file use this command
				docker-compose up -d   ->Run Docker Compose in Backend.
				docker-compose -f <Service Name> -> To View the Docker-Compose Log
