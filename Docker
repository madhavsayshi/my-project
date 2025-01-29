# Use an official Maven image as a build stage
FROM maven:3.8.6-eclipse-temurin-17 AS build

# Set working directory inside the container
WORKDIR /app

# Copy the project source code
COPY . .

# Build the application (without interactive prompts)
RUN mvn -B clean package

# Use a minimal JDK image for runtime
FROM eclipse-temurin:17-jre

# Set working directory inside the container
WORKDIR /app

# Copy the built JAR from the previous stage
COPY --from=build /app/target/*.jar app.jar

# Expose the application port (change based on your app)
EXPOSE 8080

# Run the application
CMD ["java", "-jar", "app.jar"]