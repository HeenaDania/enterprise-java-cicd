# Use a minimal, secure base image for Java 17
FROM eclipse-temurin:17-jre-alpine

# Add a non-root user for security
RUN addgroup -S spring && adduser -S spring -G spring

WORKDIR /app

# Copy only the built JAR into the image
COPY target/*.jar app.jar

# Set permissions and switch to non-root user
RUN chown spring:spring /app/app.jar
USER spring:spring

# Expose the application port (change if you use a different port)
EXPOSE 8080

# Use JVM flags for better container behavior (optional)
ENTRYPOINT ["java", "-XX:+UseContainerSupport", "-jar", "app.jar"]
