FROM eclipse-temurin:21-jre

ARG artifact=target/spring-boot-web.jar

WORKDIR /opt/app

# Copy mvnd zip from build context
COPY apache-mvnd-1.0.2-linux-amd64.zip /tmp/

# Install unzip only and extract mvnd from local copy
RUN apt-get update && \
    apt-get install -y --no-install-recommends unzip && \
    unzip /tmp/apache-mvnd-1.0.2-linux-amd64.zip -d /opt && \
    mv /opt/apache-mvnd-1.0.2-linux-amd64 /opt/mvnd && \
    ln -s /opt/mvnd/bin/mvnd /usr/bin/mvnd && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

# Copy your application JAR
COPY ${artifact} app.jar

ENTRYPOINT ["java","-jar","app.jar"]
