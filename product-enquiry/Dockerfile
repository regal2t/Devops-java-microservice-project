# biuld
FROM maven:3.8.4-openjdk-17-slim AS builder
WORKDIR /app
COPY . .
RUN mvn clean package

#run
FROM adoptopenjdk/openjdk14:alpine-jre AS runtime
COPY --from=builder /app/target/*.jar /app.jar
ENV JAVA_OPTS=""
EXPOSE 8700
ENTRYPOINT ["sh", "-c", "java $JAVA_OPTS -Djava.security.egd=file:/dev/./urandom -jar /app.jar"]