FROM jenkins/jenkins:lts

USER root

# Install required base tools
RUN apt-get update && \
    apt-get install -y curl gnupg ca-certificates lsb-release

# Install NodeJS 18 (official method for Debian)
RUN curl -fsSL https://deb.nodesource.com/setup_18.x | bash - && \
    apt-get install -y nodejs

# Install Docker CLI only (not full engine)
RUN apt-get install -y docker.io

# Install Trivy (force bookworm repo)
RUN curl -fsSL https://aquasecurity.github.io/trivy-repo/deb/public.key | gpg --dearmor -o /usr/share/keyrings/trivy.gpg && \
    echo "deb [signed-by=/usr/share/keyrings/trivy.gpg] https://aquasecurity.github.io/trivy-repo/deb bookworm main" | tee /etc/apt/sources.list.d/trivy.list && \
    apt-get update && \
    apt-get install -y trivy

USER jenkins
