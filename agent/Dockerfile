# Start with the official Jenkins inbound agent image
FROM jenkins/inbound-agent

# Switch to root to install Docker
USER root

# Install Docker CLI
RUN apt-get update && \
    apt-get install -y docker.io && \
    rm -rf /var/lib/apt/lists/*

# Entry point to start the Jenkins agent with required arguments
# This entry point is standard for `jenkins/inbound-agent` and will
# run the Jenkins agent service automatically on container start
ENTRYPOINT ["jenkins-agent"]
