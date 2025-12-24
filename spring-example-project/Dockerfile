FROM eclipse-temurin:21-jdk-alpine-3.23 AS build-stage

EXPOSE 8080

WORKDIR /usr/src/app

COPY . .

RUN chmod +x mvnw && adduser -D java-user && chown java-user -R .

USER java-user

RUN ./mvnw package

#CMD ["java", "-jar", "./target/docker-example-1.1.3.jar"]

FROM eclipse-temurin:21-jre-alpine-3.23

EXPOSE 8080

WORKDIR /app

COPY --from=build-stage /usr/src/app/target/docker-example-1.1.3.jar docker.jar

RUN adduser -D java-user && chown java-user -R .

USER java-user

CMD ["java", "-jar", "./docker.jar"]


