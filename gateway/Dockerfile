FROM maven:3.8.1-openjdk-17-slim AS build
WORKDIR /gateway
COPY pom.xml .
COPY src ./src
RUN mvn clean package -DskipTests

FROM openjdk:17-jdk-slim
WORKDIR /gateway
COPY --from=build /gateway/target/*.jar gateway.jar
ENTRYPOINT ["java","-jar","gateway.jar"]
