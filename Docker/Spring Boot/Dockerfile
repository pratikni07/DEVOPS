# Stage 1: Build Stage
FROM maven:3.8.6-openjdk-17-slim AS build
# Set working directory
WORKDIR /app
# Copy pom.xml 
COPY pom.xml .
# Download 
RUN mvn clean install

# Copy the source code
COPY src ./src

# Build the Spring Boot application
RUN mvn clean package -DskipTests

# Stage 2: Production Stage
FROM openjdk:17-jdk-slim

# Set working directory
WORKDIR /app

# Copy the packaged .jar file from the build stage
COPY --from=build /app/target/*.jar /app/app.jar

# Expose the application port (default Spring Boot port is 8080)
EXPOSE 8080

# Health Check using Spring Boot Actuator's /actuator/health endpoint
HEALTHCHECK --interval=30s --timeout=10s --retries=3 \
  CMD curl --silent --fail http://localhost:8080/actuator/health || exit 1

# Run the Spring Boot application
CMD ["java", "-jar", "/app/app.jar"]
