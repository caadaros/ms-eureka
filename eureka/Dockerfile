# Etapa 1: Construcción
FROM maven:3.9.6-eclipse-temurin-21-alpine AS builder
WORKDIR /app

# Copiamos todo el proyecto
COPY . .

# Compilamos usando el Maven global de la imagen (sin usar ./mvnw)
RUN mvn clean package -DskipTests -q

# Etapa 2: Ejecución
FROM eclipse-temurin:21-jre-alpine
WORKDIR /app
COPY --from=builder /app/target/*.jar app.jar
EXPOSE 8761
ENTRYPOINT ["java", "-jar", "app.jar"]