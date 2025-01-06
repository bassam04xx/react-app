# Use an official Jenkins image
FROM jenkins/jenkins:lts-slim

# Install necessary plugins for Docker and Git
RUN jenkins-plugin-cli --plugins "docker-workflow:latest" "git:latest" "pipeline-model-definition:latest"
# Install Docker (to be able to build Docker images from within Jenkins)
USER root
RUN apt-get update && apt-get install -y \
    docker.io \
    sudo \
    && rm -rf /var/lib/apt/lists/*

# Add Jenkins user to the docker group (so Jenkins can use Docker)
RUN usermod -aG docker jenkins

USER jenkins

# Expose port for Jenkins
EXPOSE 8080

