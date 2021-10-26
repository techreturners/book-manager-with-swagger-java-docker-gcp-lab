# Activity 1

## 🗺 Exploration

## 🔎 Exercise 1.1 - Exploring the Code

If you have previously created a Java Spring application then most of the files should look familiar.

However there is one new file to point out and that is the [Dockerfile](../Dockerfile).

The Dockerfile looks like this:

```dockerfile
FROM amazoncorretto:11-alpine3.14-jdk
RUN addgroup -S spring && adduser -S spring -G spring
USER spring:spring
ARG JAR_FILE=target/*.jar
COPY ${JAR_FILE} app.jar
ENTRYPOINT ["java","-jar","/app.jar"]
```
