# Activity 1

## 🗺 Exploration

## 🔎 Exercise 1.1 - Exploring the Code

If you have previously created a Java Spring application then most of the files should look familiar.

However, there is one new file to point out and that is the [Dockerfile](../Dockerfile).

The Dockerfile looks like this:

```dockerfile
FROM amazoncorretto:11-alpine3.14-jdk
RUN addgroup -S spring && adduser -S spring -G spring
USER spring:spring
ARG JAR_FILE=target/*.jar
COPY ${JAR_FILE} app.jar
ENTRYPOINT ["java","-jar","/app.jar"]
```
- What do you think might be happening in the first line of that Dockerfile?

<details>
<summary>Click here to see the answer</summary>
<pre>

Think of Docker [images](https://docs.docker.com/glossary/#image) like layers of an onion. 

We can create Docker images that build upon previous layers. 

The first line of this particular Dockerfile tells Docker build 
on a Java image provided on the [DockerHub](https://hub.docker.com/_/amazoncorretto) by Amazon.

That particular image makes sure the version 11 of the 
Java Development Kit is present.

</pre>
</details>

Wait....hold up....in the answer you mentioned the [Docker Hub](https://hub.docker.com). What is the Docker Hub?!

The Docker hub is a public site where you can publish Docker images. You can make them publicly available for the community to use.

Very similar to the Java dependencies you've got in your code. Those Java dependencies get pulled from the Maven Central servers. 

Well in Docker that image (`amazoncorretto:11-alpine3.14-jdk`) we've "based" our Dockerfile from gets "pulled" from the Docker Hub.

In container talk, the Docker Hub is known as a **Container Registry** but more on that later...

Moving on to the following two lines:

```dockerfile
RUN addgroup -S spring && adduser -S spring -G spring
USER spring:spring
```

Well those two lines run instructions within the container image. The `RUN` instruction tells the image to add a user and a group called "spring" to the operating system.

Much like you would when adding a new user to your own computer. Then the `USER` instruction tells Docker to use the **spring** user for all following commands.

This is a bit of security, making sure we're not running our Java application using the **root** user.

The next two lines look complicated but are just a fancy way of saying copy a file from my local computer (your computer) into the Docker image

```dockerfile
ARG JAR_FILE=target/*.jar
COPY ${JAR_FILE} app.jar
```

The file it copies is a **JAR** file located in the target directory. The JAR file is what is produced when you build your Spring boot application.

It stands for **J**ava **AR**chive.

Then the final line is the powerful one. An `ENTRYPOINT` instruction tells Docker what command should be executed when starting the container.

```dockerfile
ENTRYPOINT ["java","-jar","/app.jar"]
```

Essentially this says, when the docker container runs please run the command `java -jar /app.jar`. Just like you might do on your local computer.

Now we've had a bit of an explore, I expect you're excited to get build a docker image and getting it running.

Head over to [Activity 2](./activity_2.md) and we can get things built and running.
