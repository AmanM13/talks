# [FOSS Meetup Bangalore April 2024](https://forum.fossunited.org/t/foss-meetups-bangalore-2024/2702/30)
- **Title** - Mastering Docker: A Comprehensive Workshop for Beginners - [Slides](https://docs.google.com/presentation/d/11fkX9zqdkD2BZ8GmhYNu5RbNhQCSeN_5KXguUjUkOzs)
- **Date** - April 27th, 2024
- **Mode** - In-person
### Prerequisites
- 💻 BYOD / Laptop
- 🐳 Docker Hub account - [steps](https://kubedaily.com/docs/docker/docker-prerequisites/#:~:text=Here%20are%20the%20steps%20to%20create%20a%20Docker%20Hub%20account%3A)
- 🆓 Lab options
  1. [Play with Docker](https://labs.play-with-docker.com/) ( 4 hour time window, small terminal)
  2. [Killercoda](https://killercoda.com/playgrounds/scenario/ubuntu) ( 1 hour time window, full screen terminal, IDE )
### Getting started
Say hello-world👋
```
docker run hello-world
```
2️⃣0️⃣4️⃣8️⃣ container game🎮 for fun!
```
docker run -d -p 8080:80 alexwhen/docker-2048
```
Open port 8080 in your lab environment and enjoy :)
### Let's build our first container image using Docker🚀
Create Dockerfile
```
vi Dockerfile
```
Copy and paste the below
```
# Use an existing image as a base
FROM nginx:alpine

# Set working directory
WORKDIR /usr/share/nginx/html

# Set the content of index.html directly
RUN echo "Hello from FOSS Bangalore!" > index.html

# Expose port 80
EXPOSE 80
```
Press `:wq!` and enter to save and exit

Build image
```
docker build -t your_image_name:tag .
```
Example
```
docker build -t foss-meetup-bangalore:v1 .
```
Check built image
```
docker images
```
Output
```
REPOSITORY              TAG       IMAGE ID       CREATED         SIZE
foss-meetup-bangalore   v1        24396f63e519   8 seconds ago   48.3MB
```
### Running container
Run the container from the built image and map the container's 80 port to your system's 8081 port
```
docker run -d -p 8081:80 --name your_container_name your_image_name:tag
```
Example
```
docker run -d -p 8081:80 --name foss-app foss-meetup-bangalore:v1
```
Check for container's status
```
docker ps
```
Output
```
CONTAINER ID   IMAGE                      COMMAND                  CREATED         STATUS         PORTS                                   NAMES
1299e4a5a49d   foss-meetup-bangalore:v1   "/docker-entrypoint.…"   6 seconds ago   Up 5 seconds   0.0.0.0:8081->80/tcp, :::8081->80/tcp   foss-app
```
Access the application
```
curl localhost:8081
```
Output
```
Hello from FOSS Bangalore!
```
OR Open port 8081 in your lab environment
### Pushing image to Docker Hub
Create a repository in your Docker Hub account [here](https://hub.docker.com/repository/create?namespace=)

Login to docker 
```
docker login
```
Tag & push image to Docker Hub
```
docker tag your_image_name:tag username/repository_name:tag
```
Example
```
docker tag foss-meetup-bangalore:v1 rootxaman/foss-meetup-bangalore:v1
```
```
docker push username/repository_name:tag
```
Example
```
docker push rootxaman/foss-meetup-bangalore:v1
```
### Making and committing changes to container
Make changes to the running container
```
docker exec -it container_name /bin/sh
```
Example
```
docker exec -it foss-app /bin/sh
```
Output
```
/usr/share/nginx/html #
```
Let's add a new line to our webpage -> We are learning Docker.

Open index.html using `vi` editor and press `i` to enter INSERT mode
```
vi index.html
```
Updated content
```
Hello from FOSS Bangalore! <br> We are learning Docker.
```
Press `:wq!` and enter to save and exit

After making the changes, they are updated in real-time and served. You can verify the changes by using the following command from inside the container:
```
curl localhost
```
Output
```
Hello from FOSS Bangalore! <br> We are learning Docker.
```
Exit from the container
```
exit
```
Changes can also be verified from outside the container
```
curl localhost:8081
```
Output
```
Hello from FOSS Bangalore! <br> We are learning Docker.
```
OR Open port 8081 in your lab environment

Commit changes and create a new image from the container (running)
```
docker commit container_name your_image_name:new_tag
```
Example
```
docker commit foss-app foss-meetup-bangalore:v2
```
Tag the new image
```
docker tag your_image_name:new_tag username/repository_name:new_tag
```
Example
```
docker tag foss-meetup-bangalore:v2 rootxaman/foss-meetup-bangalore:v2
```
Push the new image to Docker Hub
```
docker push username/repository_name:new_tag
```
Example
```
docker push rootxaman/foss-meetup-bangalore:v2
```
Run a container using the new image
```
docker run -d -p 8082:80 --name new_container_name username/repository_name:new_tag
```
Example 
```
docker run -d -p 8082:80 --name foss-app-2 rootxaman/foss-meetup-bangalore:v2
```
```
curl localhost:8082
```
Output
```
Hello from FOSS Bangalore! <br> We are learning Docker.
```
OR Open port 8082 in your lab environment

## Congratulations and Summary

Congratulations on completing the "Mastering Docker: A Comprehensive Workshop for Beginners" at FOSS Meetup Bangalore April 2024! 🎉

### Summary of Learnings:

- **Getting Started**: We started with the basics of Docker by running the "hello-world" container and enjoying the "2048" container game.
- **Building Our First Container Image**: We created a custom Docker image using a Dockerfile to serve a webpage with the message "Hello from FOSS Bangalore!".
- **Running and Testing the Container**: We ran our container, mapped it to a host port, and verified the webpage using `curl` or by opening the port in our lab environment.
- **Pushing Image to Docker Hub**: We learned how to push our Docker image to Docker Hub, making it accessible to others.
- **Making and Committing Changes to Container**: We explored how to make changes to a running container, update its content, and commit those changes to create a new Docker image.
- **Deploying a New Container with Updated Image**: Finally, we deployed a new container using the updated Docker image and verified the changes.

### Next Steps:

Continue exploring Docker and its ecosystem! Experiment with different Docker commands, explore container orchestration with Docker Compose or Kubernetes, and dive deeper into containerized application development.

Once again, congratulations on your journey into Docker! We hope you found this workshop valuable and look forward to seeing what you build with Docker in the future.

Happy Dockering! 🐳✨


