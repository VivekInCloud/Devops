#### Containers
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
  * Operating system level virtualization is where an operating system kernel can support multiple isolated user space instances
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
