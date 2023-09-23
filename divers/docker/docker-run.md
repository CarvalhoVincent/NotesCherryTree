# Docker run

The Docker run command creates running containers from images. This is where commands from the Dockerfile (as well as our own input at runtime) are run. Because of this, it must be some of the first syntaxes you learn.\
The command works in the following way: `docker run [OPTIONS] IMAGE_NAME [COMMAND] [ARGUMENTS...]` the options enclosed in brackets are not required for a container to run.\
Docker containers can be run with various options - depending on how we will use the container. This task will explain some of the most common options that you may want to use.

### First, Simply Running a Container

Let's recall the syntax required to run a Docker container: `docker run [OPTIONS] IMAGE_NAME [COMMAND] [ARGUMENTS...]` . In this example, I am going to configure the container to run:

• An image named "helloworld"\
• "Interactively" by providing the `-it` switch in the \[OPTIONS] command. This will allow us to interact with the container directly.\
• I am going to spawn a shell within the container by providing `/bin/bash` as the \[COMMAND] part. This argument is where you will place what commands you want to run within the container (such as a file, application or shell!)

So, to achieve the above, my command will look like the following: `docker run -it helloworld /bin/bash`\
A terminal showing a container being launched in 'interactive' mode\
`cmnatic@thm-intro-to-docker:~$ docker run -it helloworld /bin/bash`\
`root@30eff5ed7492:/#`

We can verify that we have successfully launched a shell because our prompt will change to another user account and hostname. The hostname of a container is the container ID (which can be found by using `docker ps`). For example, in the terminal above, our username and hostname are `root@30eff5ed7492`

### Running Containers...Continued

As previously mentioned, Docker containers can be run with various options. The purpose of the container and the instructions set in a Dockerfile (we'll come onto this in a later task) determines what options we need to run the container with. To start, I've put some of the most common options you may need to run your Docker container into the table below.

| \[OPTION] | Explanation                                                                                                                                                                                                                                                                                                              | Relevant Dockerfile Instruction | Example                                                          |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------- | ---------------------------------------------------------------- |
| -d        | This argument tells the container to start in "detached" mode. This means that the container will run in the background.                                                                                                                                                                                                 | N/A                             | docker run -d helloworld                                         |
| -it       | This argument has two parts. The "i" means run interactively, and "t" tells Docker to run a shell within the container. We would use this option if we wish to interact with the container directly once it runs.                                                                                                        | N/A                             | docker run -it helloworld                                        |
| -v        | This argument is short for "Volume" and tells Docker to mount a directory or file from the host operating system to a location within the container. The location these files get stored is defined in the Dockerfile                                                                                                    | VOLUME                          | docker run -v /host/os/directory:/container/directory helloworld |
| -p        | This argument tells Docker to bind a port on the host operating system to a port that is being exposed in the container. You would use this instruction if you are running an application or service (such as a web server) in the container and wish to access the application/service by navigating to the IP address. | EXPOSE                          | docker run -p 80:80 webserver                                    |
| --rm      | This argument tells Docker to remove the container once the container finishes running whatever it has been instructed to do.                                                                                                                                                                                            | N/A                             | docker run --rm helloworld                                       |
| --name    | This argument lets us give a friendly, memorable name to the container. When a container is run without this option, the name is two random words. We can use this open to name a container after the application the container is running.                                                                              | N/A                             | docker run --name helloworld                                     |

These are just some arguments we can provide when running a container. Again, most arguments we need to run will be determined by how the container is built. However, arguments such as `--rm` and `--name` will instruct Docker on how to run the container. Other arguments include (but are not limited to!):\
◇ Telling Docker what network adapter the container should use\
◇ What capabilities the container should have access to. This is covered in the "[Docker Rodeo](https://tryhackme.com/room/dockerrodeo)" room on TryHackMe.\
◇ Storing a value into an environment variable

If you wish to explore more of these arguments, I highly suggest reading the [Docker run documentation](https://docs.docker.com/engine/reference/run/).

### Listing Running Containers

To list running containers, we can use the docker ps command. This command will list containers that are currently running - like so:\
A terminal showing a list of running containers and their information\
`cmnatic@thm:~/intro-to-docker$ docker ps`\
`CONTAINER ID IMAGE COMMAND CREATED STATUS PORTS NAMES`

`a913a8f6e30f cmnatic/helloworld:latest "sleep" 1 months ago Up 3 days 0.0.0.0:8000->8000/tcp helloworld`\
`cmnatic@thm:~/intro-to-docker$`

This command will also show information about the container, including:\
◇ The container's ID\
◇ What command is the container running\
◇ When was the container created\
◇ How long has the container been running\
◇ What ports are mapped\
◇ The name of the container

**Tip:** To list all containers (even stopped), you can use

A terminal showing a list of ALL containers and their information\
`cmnatic@thm:~/intro-to-docker$ docker ps -a`\
`CONTAINER ID IMAGE COMMAND CREATED STATUS PORTS NAMES`\
`00ba1eed0826 gobuster:cmnatic "./gobuster dir -url…" an hour ago Exited an hour ago practical_khayyam`
