FROM eclipse-temurin:21-jre

ARG artifact=target/spring-boot-web.jar

WORKDIR /opt/app

# Install required tools
RUN apt-get update && \
    apt-get install -y --no-install-recommends unzip curl && \
    curl -LO https://downloads.apache.org/maven/mvnd/1.0.2/apache-mvnd-1.0.2-linux-amd64.zip && \
    unzip apache-mvnd-1.0.2-linux-amd64.zip -d /opt && \
    mv /opt/apache-mvnd-1.0.2-linux-amd64 /opt/mvnd && \
    ln -s /opt/mvnd/bin/mvnd /usr/bin/mvnd && \
    rm apache-mvnd-1.0.2-linux-amd64.zip && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

# Copy your Spring Boot JAR
COPY ${artifact} app.jar

ENTRYPOINT ["java", "-jar", "app.jar"]
