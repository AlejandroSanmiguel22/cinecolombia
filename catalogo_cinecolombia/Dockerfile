# Usar Java 21 como imagen base
FROM openjdk:21

# Establecer el directorio de trabajo dentro del contenedor
WORKDIR /app

# Copiar el archivo JAR generado por Gradle al contenedor
COPY build/libs/catalogo_cinecolombia-0.0.1-SNAPSHOT.jar app.jar

# Copiar el script wait-for-it.sh
COPY wait-for-it.sh /app/wait-for-it.sh

# Dar permisos de ejecución al script
RUN chmod +x /app/wait-for-it.sh

# Exponer el puerto en el que correrá la aplicación Spring Boot
EXPOSE 8081

# Comando de entrada para esperar a MySQL y luego ejecutar la aplicación
ENTRYPOINT ["./wait-for-it.sh", "db:3306", "--", "java", "-jar", "app.jar"]
