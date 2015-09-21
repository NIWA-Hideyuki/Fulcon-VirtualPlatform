## Fulcon

`Fulcon` is the CLI tool for Full Container System

## State of the project

In Fulcon, the container can be handled like VM. 
Fulcon constructs the system by generating the container, logging in 
from the console, and installing the package with yum and apt, and stops 
the system with shutdown command. The container can be connected directly with 
the Internet by adding virtual NIC. 
Fulcon can handle CentOS 7 and Ubuntu 15.04

### Building:

ubuntu15.04

/$ sudo apt-get install docker.io
/$ sudo apt-get install python-ipy
/$ sudo apt-get install bridge-utils

/$ tar xzf fulcon.tgz
/$ cd fulcon
/$ sudo make install

CentOS 7

/$ sudo yum install docker-io
/$ sudo yum install python-IPy
/$ sudo yum install bridge-utils

/$ tar xzf fulcon.tgz
/$ cd fulcon
/ $ sudo make install

### Setup:

The image of CentOS 7 and Ubuntu15.04 is prepared. 

/$ sudo fulcon setup

It takes time until ending.
This operation do only first once.

The image is acquired by using Dockerfile and this command is set up. 
If it does not go well. images are generated with following Dockerfile. 
	/var/lib/fulcon/driver/dockerfile/centos7/Dockerfile
	/var/lib/fulcon/driver/dockerfile/ubuntu1504/Dockerfile
It must be builded "fulcon/centos7" and "fulcon/ubuntu1504"

### Using:

1. Generation of container

In the following example, the container "webap-server" is generated. 

/$ sudo fulcon sysgen webap-server

The container of "fulcon/centos7" was generated. 
It is optional -c, and "fulcon/ubuntu1504" can be specified. 

2. The user is added, and the password is set. 

In the following example, the user "niwa" is seted.

/$ sudo fulcon set-user webap-server niwa

3. Virtual NIC addition

/$ sudo fulcon net-add webap-server 192.168.17.2/24


4. Attache console to the container, and login in the container. 

/$ sudo fulcon console webap-server
/Attached aa-srv.
/To enter console, hit Enter.
/To exit console, ^p^q is pushed.

5. When you login the container, yum and apt can be used. 
   You can login with ssh. 
   "shutdown -h now" can be used in container.

6. Stop and start of container

/$ sudo fulcon stop webap-server

/$ sudo fulcon start webap-server

7. List containers

/$ sudo fulcon list 

8. Erase of container

/$ sudo fulcon erase webap-server


### Sub command:

	console [ -x ] [ -n REPEAT_NUMBER] NAME

	del-user NAME USERNAME

	dirver-name

	erase NAME  ...
	erase [-n REPEAT_NUMBER] NAME

	help

	image-catalog

	image-name

	list 

	net-add [-d NIC_DEVICE] [-n VETH_NUMBER] [-g GATEWAY] [-b BRIDGE] NAME IP_ADDR/MASK

	net-del [-n VETH_NUMBER] NAME
	net-del [-d NIC_DEVICE]  NAME

	net-info NAME

	resource [-c CPU] [-n CPUSET] [-m MEM] NAME 

	set-default-image [ IMAGE_NAME ]

	set-passwd NAME USERNAME

	set-user NAME USERNAME

	set-passwd

	setup

	start NAME ...
	start [-n REPEAT_NUMBER] NAME

	stop NAME  ...
	stop [-n REPEAT_NUMBER] NAME

	sysgen [ -c IMAGE ] NAME NAME ...
	sysgen [-n REPEAT_NUMBER ] [ -c IMAGE ] NAME  ...

	update



```


