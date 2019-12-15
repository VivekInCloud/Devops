Containers:

  * Containers is OS level Virtualization.
  	* Allows for multiple isolated user space instances called containers.
 	* They share a single kernel.
  	* Can be added or removed at any time.
  * Containers consist of a self contained Linux file system
	* Can be from any Linux distribution which is compatible with the host kernel.
	* Usually contain a single application such as a server
  * Operating system level virtualization is lightweight
	* Is often used in Cloud Computing
	* It is Half the Size of VM.
  * Operating system level virtualization uses a set of tools
	* A virtualization subsystem
	* A cgroup hierarchy for each container
	* The container is mounted into the File system.
  * A program inside the container is executed
	* Using chroot to restrict it to the container file system
	* The cgroup constrains use of resources and isolates the container from the rest of the system
  * OS level virtualization is where an operating system kernel can support multiple isolated user space instances
	* Instances are called containers or jails
	* There is little overhead as the kernel implements the containers
  * There are numerous implementations
	* chroot has been available in UNIX since 1982
	* FreeBSD jail
	* Linux Containers (LXC) command line tools using Linux cgroups
	* LXD a container hypervisor built on LXC
	* Docker is a suite of tools for creating and managing containers.
	* The Concept comes from Linux like Namespace,Control Group and also because of MicroService Evolvement.
	* Containerization tool runs directly on the Operating System and Hence there is no concept called "Hyper Visor".
	* Don't run two Service in Single Containers.
	
Dockers:
        * Docker is a very light-weight software container and containerization platform.
        * Docker containers provide a way to run software in isolation			
        * Docker was originally a Linux application
        * It uses the kernel container functionality.
        * It requires a 64 bit installation using a kernel version 3.10 or later
        * Docker runs on many popular Linux distributions.
        * It is available as RPM, APT, or binary versions.
   
Dockers Architecture:
  * Docker Server :- The Server that runs the Docker Daemon & this Daemon is used to Build,Run,Distribute Containers.
  * Docker Client :- 
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

