# [FOSS Meetup Bangalore April 2024](https://forum.fossunited.org/t/foss-meetups-bangalore-2024/2702/30)
- **Title**: Mastering Docker: A Comprehensive Workshop for Beginners
- **Date** - April 27th, 2024
- **Mode** - In-person
### Prerequisites
- BYOD / Laptop
- Docker Hub account - [steps](https://kubedaily.com/docs/docker/docker-prerequisites/#:~:text=Here%20are%20the%20steps%20to%20create%20a%20Docker%20Hub%20account%3A)
### Getting started
Say hello-world👋
```
docker run hello-world
```
2️⃣0️⃣4️⃣8️⃣ container game🎮 for fun!
```
docker run -d -p 8080:80 alexwhen/docker-2048
```
### Let's build our first container image🚀
Dockerfile
```
# Use an Alpine Linux base image
FROM alpine:latest

# Set an environment variable with the message
ENV MESSAGE "Hello from FOSS Bangalore!"

# Print the message when the container starts
CMD echo $MESSAGE && tail -f /dev/null
```
Build the Image
```
docker build -t your_image_name:tag .
```
Run the Container
```
docker run --name your_container_name your_image_name:tag
```
Docker Login
```
docker login
```
Create a repo in your docker hub account
Push Image to Docker Hub
```
docker tag your_image_name:tag username/repository_name:tag
```
```
docker push username/repository_name:tag
```
Make Changes to the Running Container
```
docker exec -it container_id /bin/sh
```
```
echo "Hello from FOSS Bangalore! We are learning Docker" >> /dev/stdout
```
```
exit
```
Commit Changes to Create a New Image
```
docker commit container_id your_image_name:new_tag
```
Tag the New Image
```
docker tag your_image_name:new_tag username/repository_name:new_tag
```
Push the New Image to Docker Hub
```
docker push username/repository_name:new_tag
```
Run a Container Based on the Updated Image
```
docker run --name new_container_name username/repository_name:new_tag
```
