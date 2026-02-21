# Use official OpenJDK image
FROM eclipse-temurin:17-jdk

WORKDIR /app

# Copy Maven wrapper & pom first (better caching)
COPY mvnw .
COPY .mvn .mvn
COPY pom.xml .

RUN ./mvnw dependency:go-offline

# Copy rest of project
COPY src src

# Build app
RUN ./mvnw clean package -DskipTests

# Run jar (use wildcard to match any version)
CMD ["java", "-jar", "target/Transportation-Service-back-end-0.0.1-SNAPSHOT.jar"]