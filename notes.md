# Docker | Presentation Feb 27, 2015

Containers are like extremely lightweight VMs – they allow code to run in isolation from other containers but safely share the machine’s resources, all without the overhead of a hypervisor.


Simply put, containers are great at isolating applications and services from each other while they all share resources from the same Linux OS kernel. 


## Demo

### Running multiple distros

    docker pull ubuntu
    docker run -it ubuntu bash
    $ lsb_release
    $ dpkg -l | wc -l

    docker pull debian
    docker run -it debian bash
    $ cat /etc/os-release
    $ dpkg -l | wc -l

    docker pull centos
    docker run -it centos bash
    $ cat /etc/os-release

    docker pull opensuse
    docker run -it opensuse bash
    $ cat /etc/os-release

### Running Simple NodeJS

    docker build -t centos-node-hello .
    docker run -p 9000:8000 -d centos-node-hello

### Running Jenkins

    docker pull jenkins
    # Running
    docker run -p 8080:8080 jenkins
    # Running in Persistend mode
    docker run --name myjenkins -p 8080:8080 -v /var/jenkins_home jenkins


### Some commands

    # Delete stopped containers
    docker ps -a | awk '{print $1}' | xargs --no-run-if-empty docker rm
    # Log into a container
    docker exec -it [container-id] bash
