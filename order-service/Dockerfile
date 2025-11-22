# Step 1: Use the official OpenJDK base image to build the app
FROM maven:3.8.4-openjdk-11-slim AS build

# Step 2: Set the working directory inside the container
WORKDIR /app

# Step 3: Copy the pom.xml and download the dependencies (faster layer caching)
COPY pom.xml .
RUN mvn dependency:go-offline

# Step 4: Copy the source code and build the application
COPY src ./src
RUN mvn clean package -DskipTests

# Step 5: Use a smaller JRE image to run the application
FROM openjdk:11-jre-slim

# Step 6: Set the working directory for the runtime image
WORKDIR /app

# Step 7: Copy the JAR file from the build stage
COPY --from=build /app/target/order-service.jar /app/order-service.jar

# Step 8: Expose the port that the application will run on (typically 8080 for Spring Boot)
EXPOSE 8080

# Step 9: Command to run the JAR file
CMD ["java", "-jar", "order-service.jar"]
