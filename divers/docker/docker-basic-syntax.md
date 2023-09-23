# Docker basic syntax

Docker can seem overwhelming at first. However, the commands are pretty intuitive, and with a bit of practice, you’ll be a Docker wizard in no time.

The syntax for Docker can be categorised into four main groups:\
• Running a container\
• Managing & Inspecting containers\
• Managing Docker images\
• Docker daemon stats and information

We will break down each of these categories in this task.

### Managing Docker Images

### Docker Pull

Before we can run a Docker container, we will first need an image. Recall from the “[Intro to Containerisation](https://tryhackme.com/room/introtocontainerisation)” room that images are instructions for what a container should execute. There’s no use running a container that does nothing!

In this room, we will use the Nginx image to run a web server within a container. Before downloading the image, let’s break down the commands and syntax required to download an image. Images can be downloaded using the `docker pull` command and providing the name of the image.

For example, `docker pull nginx`. Docker must know where to get this image (such as from a repository which we’ll come onto in a later task).

Continuing with our example above, let’s download this Nginx image!

A terminal showing the downloading of the "Nginx" image\
`cmnatic@thm:~$ docker pull nginx`\
`Using default tag: latest`\
`latest: Pulling from library/nginx`\
`-- omitted for brevity --`\
`Status: Downloaded newer image for nginx:latest`\
`cmnatic@thm:~$`

By running this command, we are downloading the latest version of the image titled “nginx”. Images have these labels called _tags_. These _tags_ are used to refer to variations of an image. For example, an image can have the same name but different tags to indicate a different version. I’ve provided an example of how tags are used within the table below:

<table><thead><tr><th width="150">Docker Image</th><th width="107">Tag</th><th width="267">Command Example</th><th>Explanation</th></tr></thead><tbody><tr><td>ubuntu</td><td>latest</td><td>docker pull ubuntu - IS THE SAME AS - docker pull ubuntu:latest</td><td>This command will pull the latest version of the "ubuntu" image. If no tag is specified, Docker will assume you want the "latest" version if no tag is specified. It is worth remembering that you do not always want the "latest". This image is quite literally the "latest" in the sense it will have the most recent changes. This could either fix or break your container.</td></tr><tr><td>ubuntu</td><td>22.04</td><td>docker pull ubuntu:22.04</td><td>This command will pull version "22.04 (Jammy)" of the "ubuntu" image.</td></tr><tr><td>ubuntu</td><td>20.04</td><td>docker pull ubuntu:20.04</td><td>This command will pull version "20.04 (Focal)" of the "ubuntu" image.</td></tr><tr><td>ubuntu</td><td>18.04</td><td>docker pull ubuntu:18.04</td><td>This command will pull version "18.04 (Bionic)" of the "ubuntu" image.</td></tr></tbody></table>

When specifying a tag, you must include a colon `:` between the image name and tag, for example, `ubuntu:22.04` (image:tag). Don’t forget about tags - we will return to these in a future task!

### Docker Image x/y/z

The `docker image` command, with the appropriate option, allows us to manage the images on our local system. To list the available options, we can simply do `docker image` to see what we can do. I’ve done this for you in the terminal below:

A terminal showing the various arguments we can provide with "docker image"

`cmnatic@thm:~$ docker image`

`Usage: docker image COMMAND`

`Manage images`

`Commands:`

<table><thead><tr><th width="187">command</th><th></th></tr></thead><tbody><tr><td>build</td><td>Build an image from a Dockerfile</td></tr><tr><td>history</td><td>Show the history of an image</td></tr><tr><td>import</td><td>Import the contents from a tarball to create a filesystem image</td></tr><tr><td>inspect</td><td>Display detailed information on one or more images</td></tr><tr><td>load</td><td>Load an image from a tar archive or STDIN</td></tr><tr><td>ls</td><td>List images</td></tr><tr><td>prune</td><td>Remove unused images</td></tr><tr><td>pull</td><td>Pull an image or a repository from a registry</td></tr><tr><td>push</td><td>Push an image or a repository to a registry</td></tr><tr><td>rm</td><td>Remove one or more images</td></tr><tr><td>save</td><td>Save one or more images to a tar archive (streamed to STDOUT by default)</td></tr><tr><td>tag</td><td>Create a tag TARGET_IMAGE that refers to SOURCE_IMAGE</td></tr></tbody></table>

`Run 'docker image COMMAND --help' for more information on a command.`\
`cmnatic@thm:~$`

◇ In this room, we are only going to cover the following options for docker images:\
▪ pull (we have done this above!)\
▪ ls (list images)\
▪ rm (remove an image)\
▪ build (we will come onto this in the “Building your First Container” task)

### Docker Image ls

This command allows us to list all images stored on the local system. We can use this command to verify if an image has been downloaded correctly and to view a little bit more information about it (such as the tag, when the image was created and the size of the image).

A terminal listing the Docker images that are stored on the host operating system

`cmnatic@thm:~$ docker image ls`\
`REPOSITORY TAG IMAGE ID CREATED SIZE`\
`ubuntu 22.04 2dc39ba059dc 10 days ago 77.8MB`\
`nginx latest 2b7d6430f78d 2 weeks ago 142MB`\
`cmnatic@thm:~$`

For example, in the terminal above, we can see some information for two images on the system:

| Repository | Tag    | Image ID     | Created     | Size   |
| ---------- | ------ | ------------ | ----------- | ------ |
| ubuntu     | 22.04  | 2dc39ba059dc | 10 days ago | 77.8MB |
| nginx      | latest | 2b7d6430f78d | 2 weeks ago | 142MB  |

### Docker Image rm

If we want to remove an image from the system, we can use `docker image rm` along with the name (or Image ID). In the following example, I will remove the "_ubuntu_" image with the tag "_22.04_". My command will be `docker image rm ubuntu:22.04`:

It is important to remember to include the _tag_ with the image name.

A terminal displaying the untagging of an image

`cmnatic@thm:~$ docker image rm ubuntu:22.04`\
`Untagged: ubuntu:22.04`\
`Untagged: ubuntu@sha256:20fa2d7bb4de7723f542be5923b06c4d704370f0390e4ae9e1c833c8785644c1`\
`Deleted: sha256:2dc39ba059dcd42ade30aae30147b5692777ba9ff0779a62ad93a74de02e3e1f`\
`Deleted: sha256:7f5cbd8cc787c8d628630756bcc7240e6c96b876c2882e6fc980a8b60cdfa274`\
`cmnatic@thm:~$`

If we were to run a `docker image ls`, we would see that the image is no longer listed:

A terminal confirming that our Docker image has been deleted\
`cmnatic@thm:~$ docker image ls`\
`REPOSITORY TAG IMAGE ID CREATED SIZE`\
`nginx latest 2b7d6430f78d 2 weeks ago 142MB`\
`cmnatic@thm:~$`
