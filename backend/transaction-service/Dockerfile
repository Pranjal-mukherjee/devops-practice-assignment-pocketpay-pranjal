FROM maven:3.8.4-openjdk-11-slim AS MAVEN_JAR
WORKDIR /code
COPY . .
RUN mvn clean package -DskipTests
 


FROM openjdk:17-jdk-alpine
WORKDIR /opt
COPY --from=MAVEN_JAR /code/target/*.jar /opt/web.jar
EXPOSE 9003
ENTRYPOINT ["java","-jar","/opt/web.jar"]