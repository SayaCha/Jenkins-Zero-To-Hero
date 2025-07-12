FROM maven:3.9.6-eclipse-temurin-17

# Install dependencies and mvnd
RUN apt-get update && apt-get install -y unzip curl && \
    curl -LO https://downloads.apache.org/maven/mvnd/0.9.0/apache-mvnd-0.9.0-linux-amd64.zip && \
    unzip apache-mvnd-0.9.0-linux-amd64.zip -d /opt && \
    mv /opt/apache-mvnd-0.9.0-linux-amd64 /opt/mvnd && \
    ln -s /opt/mvnd/bin/mvnd /usr/bin/mvnd && \
    rm apache-mvnd-0.9.0-linux-amd64.zip

ENV PATH="/opt/mvnd/bin:$PATH"

# Keeps container alive for Jenkins pipeline
CMD ["tail", "-f", "/dev/null"]
