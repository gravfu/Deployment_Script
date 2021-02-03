FROM maven:3.5-jdk-8-alpine as builder

COPY ./pom.xml ./pom.xml
RUN mvn dependency:resolve
COPY ./src ./src
RUN mvn package

FROM openjdk:8-jre-alpine
WORKDIR /app
COPY --from=builder target/file.jar ./
CMD ["java", "-jar", "file.jar"]