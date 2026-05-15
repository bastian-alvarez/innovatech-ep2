# ETAPA 1: Compilación (Build)
FROM maven:3.9.0-eclipse-temurin-17-alpine AS builder
WORKDIR /app
# Copiamos solo el pom.xml primero para aprovechar el caché de Docker
COPY pom.xml .
# Descargamos las dependencias (se guardan en caché si el pom no cambia)
RUN mvn dependency:go-offline
# Copiamos el código fuente y compilamos
COPY src ./src
RUN mvn clean package -DskipTests && rm -rf ~/.m2/repository

# ETAPA 2: Ejecución (Run) - Imagen ligera
FROM eclipse-temurin:17-jre-alpine
WORKDIR /app

# RÚBRICA: Crear un usuario sin privilegios (no-root)
RUN addgroup -S appgroup && adduser -S appuser -G appgroup
USER appuser

# RÚBRICA: Copiar solo el artefacto final desde la Etapa 1
COPY --from=builder /app/target/*.jar app.jar

# Exponemos el puerto (por defecto Spring Boot usa 8080)
EXPOSE 8080

ENTRYPOINT ["java", "-jar", "app.jar"]