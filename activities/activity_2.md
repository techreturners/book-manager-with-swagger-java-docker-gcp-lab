# Activity 2

## 🛠 Building and Running

## 💿 Exercise 2.1 - Installing Docker

In order to build and run Docker containers we'll need to install Docker.

Thankfully Docker provide installers for various operating machines

Head over to their website and install **Docker Desktop** on to your computer

**NOTE:** You DO NOT have to pay or sign up for any paid subscription to complete this lab. 

https://www.docker.com/get-started

## 💻 Exercise 2.2 - Validating installation

Once you have successfully installed Docker Desktop you should be able to run docker images from the terminal

Have a go now and see if you can see you docker version by running the `docker --version` command.

You should see something similar to:

```
docker --version

Docker version 20.10.6, build 370c289
```

## 🎨 Exercise 2.3 - Reviewing images

You can now utilise docker commands

Let's have a look at the docker images you have on your computer.

```
docker images
```

If you don't have any images yet, you'll see something like this:

```
docker images

REPOSITORY   TAG       IMAGE ID   CREATED   SIZE
```

## 🧰 Exercise 2.4 - Building your image

Now the exciting part, lets build your first docker image.

Make sure you are in the root of your project (essentially where the Dockerfile is located) and run the following command:

```
docker build -t book-manager-api:1.0 .
```

You should Docker start to build your image. It might take a few minutes whilst it pulls down (downloads) the base images required.

Now try the `docker images` command again. Lets see if the image is there. You should see something similar to:

```
docker images

REPOSITORY         TAG       IMAGE ID       CREATED             SIZE
book-manager-api   1.0       37b00ee85718   About an hour ago   371MB
```
