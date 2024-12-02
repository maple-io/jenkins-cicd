FROM jenkins/inbound-agent:latest-jdk17

# Install Docker CLI
USER root
RUN apt-get update && apt-get install -y docker.io && rm -rf /var/lib/apt/lists/*

# Add Jenkins user to the docker group if it exists, or create the group if not
RUN getent group docker || groupadd -g 999 docker && usermod -aG docker jenkins

# Switch back to Jenkins user
USER jenkins