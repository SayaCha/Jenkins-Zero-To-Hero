FROM eclipse-temurin:21-jre

# Set artifact location (jar built by Maven)
ARG artifact=target/spring-boot-web.jar

# Create working directory
WORKDIR /opt/app

# Install curl and unzip, download mvnd, clean up afterward
RUN apt-get update && \
    apt-get install -y --no-install-recommends unzip curl && \
    curl -LO https://downloads.apache.org/maven/mvnd/0.9.0/apache-mvnd-0.9.0-linux-amd64.zip && \
    unzip apache-mvnd-0.9.0-linux-amd64.zip -d /opt && \
    mv /opt/apache-mvnd-0.9.0-linux-amd64 /opt/mvnd && \
    ln -s /opt/mvnd/bin/mvnd /usr/bin/mvnd && \
    rm apache-mvnd-0.9.0-linux-amd64.zip && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

# Copy your built JAR into the image
COPY ${artifact} app.jar

# Default command
ENTRYPOINT ["java","-jar","app.jar"]
