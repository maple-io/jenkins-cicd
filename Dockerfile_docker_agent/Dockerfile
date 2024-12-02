FROM jenkins/inbound-agent:latest-jdk17

# Install Docker CLI
USER root
RUN apt-get update && apt-get install -y docker.io && rm -rf /var/lib/apt/lists/*

# Check if 'docker' group exists, and create it if not
ARG DOCKER_GID=999
RUN getent group docker || groupadd -g ${DOCKER_GID} docker && usermod -aG docker jenkins

# Switch back to Jenkins user
USER jenkins