

FROM openjdk:22-jdk
ADD target/heroku-demo.jar herolu-demo.jar
ENTRYPOINT ["java","-jar","/heroku-demo.jar"]

#
# Build stage
#
FROM maven:3.8.2-jdk-11 AS build
COPY . .
#RUN mvn clean package -Pprod -DskipTests

#
# Package stage
#
FROM openjdk:11-jdk-slim
COPY --from=build /target/heroku-demo.jar demo.jar
# ENV PORT=8080
EXPOSE 8080
ENTRYPOINT ["java","-jar","demo.jar"]