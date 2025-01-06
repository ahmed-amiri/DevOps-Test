# Use a base image with OpenJDK 17 (or your version of choice)
FROM openjdk:17-jdk-slim as build

# Set the working directory
WORKDIR /app

# Copy the Maven wrapper and the pom.xml file
COPY mvnw .
COPY .mvn .mvn
COPY pom.xml .

# Add executable permissions to the Maven Wrapper
RUN chmod +x mvnw

# Download the project dependencies (this step avoids re-downloading them if they haven't changed)
RUN ./mvnw dependency:go-offline

# Copy the rest of the project files
COPY src /app/src

# Build the application
RUN ./mvnw clean package -DskipTests

# Use a smaller base image for running the application
FROM openjdk:17-jdk-slim

# Set the working directory
WORKDIR /app

# Copy the JAR file built from the previous step
COPY --from=build /app/target/thebackend-0.0.1-SNAPSHOT.jar /app/thebackend.jar

# Expose the port the app will run on
EXPOSE 8080

# Command to run the Spring Boot app
ENTRYPOINT ["java", "-jar", "/app/thebackend.jar"]
