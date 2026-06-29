# Etapa 1: Construcción
FROM eclipse-temurin:21-jdk-alpine AS builder
WORKDIR /app
# Copia absolutamente todo lo que esté en la raíz de tu GitHub al contenedor
COPY . .
# Da permisos de ejecución al wrapper de Maven y compila
RUN chmod +x mvnw && ./mvnw clean package -DskipTests -q

# Etapa 2: Ejecución (Imagen ligera)
FROM eclipse-temurin:21-jre-alpine
WORKDIR /app
# Copia el archivo JAR generado en la etapa anterior
COPY --from=builder /app/target/*.jar app.jar
EXPOSE 8761
ENTRYPOINT ["java", "-jar", "app.jar"]