FROM maven:3.9.6-eclipse-temurin-17 AS build
WORKDIR /app
COPY pom.xml .
RUN mvn -q dependency:go-offline
COPY src src
RUN mvn -q package -DskipTests

FROM eclipse-temurin:17-jre
WORKDIR /app
COPY --from=build /app/target/metadata-search-0.0.1.jar app.jar
EXPOSE 8085
ENTRYPOINT ["java","-jar","/app/app.jar"]