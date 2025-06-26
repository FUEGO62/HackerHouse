# Use official Maven image to build the app
FROM maven:3.9.6-eclipse-temurin-21 AS build

# Set working directory
WORKDIR /app

# Copy source code
COPY . .

# Build the application
RUN mvn clean package -DskipTests

# Use lightweight JDK image to run the app
FROM eclipse-temurin:21-jdk-alpine

WORKDIR /app

# Copy jar from build stage
COPY --from=build /app/target/hackerHouse-1.0-SNAPSHOT.jar app.jar

# Expose port (Render uses $PORT)
EXPOSE 8080

# Use environment variable PORT if available
ENV PORT=8080

# Run the jar file
CMD ["java", "-jar", "app.jar"]
