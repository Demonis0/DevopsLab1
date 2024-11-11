# Start with the official Jenkins inbound agent image
FROM jenkins/inbound-agent

# Switch to root to install Docker and Docker Compose
USER root

# Install Docker CLI and dynamically fetch the latest Docker Compose release
RUN apt-get update && \
    apt-get install -y docker.io curl && \
    LATEST_COMPOSE_VERSION=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep '"tag_name":' | sed -E 's/.*"([^"]+)".*/\1/') && \
    curl -L "https://github.com/docker/compose/releases/download/${LATEST_COMPOSE_VERSION}/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose && \
    chmod +x /usr/local/bin/docker-compose && \
    rm -rf /var/lib/apt/lists/*

# Set entry point to start the Jenkins agent with required arguments
ENTRYPOINT ["jenkins-agent"]
