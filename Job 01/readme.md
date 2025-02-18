# Runtrack Job 01 : Docker

```sh
docker version
```
This command allows us to check which version of docker we're using.


![alt text](<images_docker/docker_version.png>)


```sh
docker info
```
Displays system wide information regarding the Docker installation 

![alt text](<images_docker/docker_info.png>)

```sh
docker ps
```
Provides a list of containers on your machine as well as their specific state (running or not, size..)

![alt text](<images_docker/docker_ps.png>)

```sh
docker images
```
Displays a list of the images you pulled and their satuts.

![alt text](<images_docker/docker_images.png>)

```sh
docker run
```

Starts a new container and executes a command inside it, it pulls an image if needed. 

![alt text](<images_docker/docker_run.png>)

```sh
docker stop
```
Stops one or more running containers.

![alt text](<images_docker/docker_stop.png>)

```sh
docker pull
```
The "docker pull" command downloads a Docker image locally on the host from a public or private registry. Here we pulled nginx's latest image version using the ":latest" option.

![alt text](<images_docker/docker_pull.png>)

```sh
docker images
```
As said previously, this command displays all of your images. Since we pulled nginx's image, we can see where it's saved locally, which version we're using, its ID, when it was created and how much space it takes. 

![alt text](<images_docker/docker_images_exemple.png>)

```sh
docker run <image_name>
```

Using docker run to create container for nginx's image. `-it`option allows to run the container interacively. `-i` for interactive mode and `-t` for accessing terminal. This can be useful if the image you're running is an OS for exemple.

  ```--rm``` option makes it so this container will be deleted if stopped. 

  `-p` is used to assign a port for your image.

![alt text](<images_docker/docker_run_exemple.png>)

```sh
Access container using an explorer
``` 
To acces your container using an exploreur, we use the port we assigned it as an url in the search tab.

![alt text](<images_docker/docker_explorer_url.png>)

![alt text](<images_docker/nginx_explorer.png>)

```sh
docker stop <container_name>
```
This command allows us to stop a running container with its name. We can use the `docker ps` command to retrieve the name of the container and then use it.

![alt text](images_docker/docker_stop_exemple.png)


```sh
docker rm <container_name>
```

Deletes a specific container. Here as we used the `--rm` option creating the container, it was deleted when stopped. We get an error message as it no longer exists.

![alt text](images_docker/docker_rm.png)


```sh
docker rmi <image_name>
```

This command deletes a specific image. 

![alt text](images_docker/docker_rmi.png)


```sh
docker rm <container_name>
```

This command deletes a specific container

![alt text](images_docker/docker_stop_then_rm.png)

I have created 3 containers beforehand then stopped and deleted the one named "container_1".

`docker ps -a`allows us to see all containers, including does we stopped. We can see that "container_1" is deleted completely after we used the command. 

You can also combine both command to make it in one line like so (windows powershell):

![alt text](images_docker/docker_stop_and_rm.png)

To delete multiple contenairs we just write all the names of those we want deleted after the command, separate with space, like so :

 ![alt text](images_docker/docker_rm_multiple.png)

```sh
docker container prune
```

We check chich container are stopped using `ps -a` then use the command to delete them.
Once it's done we can check again with `ps -a` to see if all went well.

![alt text](images_docker/docker_container_prune.png)

```sh
docker rm -f <contenair_name/ID>
```

This command forcefully deletes a container whether it's running or not so you don't need to stop it beforehand. You can use it with the container's name or ID.

![alt text](images_docker/docker_rm_f.png)

```sh
docker rmi <image_name>
```
To delete a specific image you need to stop and delete all containers using it then use the `docker rmi`command. 

![alt text](images_docker/docker_rmi_exemple.png)

```sh
docker rmi <image_name> <image_name>
```
To delete multiple images, use the same command and process as before and write every image you want to delete seperated with space after the command.

![alt text](images_docker/docker_rmi_multiple_exemple.png)

```sh
docker image prune -a
```

This command will delete all images that aren't in use.

![alt text](images_docker/docker_image_prune_a.png)


```sh
docker rmi -f $(docker images -q)
```

Once every container running with any image has been stopped, this command will let you force delete said images. Images CANNOT be deleted if the containers running them aren't stopped. You can use this command : `docker stop $(docker ps -q)` to stop every running containers beforehand.

![alt text](images_docker/docker_rmi_running.png)

