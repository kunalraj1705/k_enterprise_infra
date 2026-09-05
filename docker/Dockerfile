FROM maven:3.9-eclipse-temurin-25 AS build

WORKDIR /build

COPY pom.xml .
COPY src ./src

RUN mvn clean package -DskipTests

FROM eclipse-temurin:25-jre

WORKDIR /app

COPY --from=build /build/target/k_enterprise-0.0.1-SNAPSHOT.jar app.jar

ENTRYPOINT ["java", "-jar", "app.jar"]
