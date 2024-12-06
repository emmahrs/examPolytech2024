FROM maven:3.9-eclipse-temurin-8-alpine as builder

LABEL maintainer="emma"

WORKDIR /app

COPY . .

RUN mvn clean package -DskipTests


FROM eclipse-temurin:8-jre

WORKDIR /app

COPY --from=builder /app/target/*.jar app.jar

EXPOSE 8448

CMD ["java", "-jar", "app.jar"]












