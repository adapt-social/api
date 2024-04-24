# About Docker

## Meanings of the different parts of a Dockerfile

&nbsp;

**First steps**

To start you need the Docker app on your computer. So go to the appstore / playstore and download Docker.

&nbsp;

**Build the app's image**

- For building the image you need a Dockerfile
- A Dockerfile is a textbased file that contains a script of instructions
- Make sure you are on the level of the directory where package.json is
- To finally build the image use the following command:

`docker build -t image-name .`

- `docker build ` : uses the Dockerfile to build a new image
- `-t ` : tags the image with a name that you can use to refer to this image when you run a container
- `.` : the dot tells Docker that it should look for the Dockerfile in the current directory

&nbsp;

**Start and app container**

- When you have an image you can run the application in a container
- You are doing this with the docker run command

`docker run -dp 127.0.0.1:3000:3000 image-name`

- `-d` : Short for "detach" and is used to run your container in the background and gives you an empty terminal
- `-p` : Short for "publish", creates a port mapping between the host and the container. Without port mapping, you wouldn't be able to access the application from the host.
- `127.0.0.1:3000` : port of your
- have the Docker app running in the background
- You should see at least one container running that's using the _image-name_ image on port 3000
- To check you can use the Docker Desktop or terminal (for terminal run the command docker ps)

![Docker Desktop with running container](./assets/dashboard-two-containers.jpg)
