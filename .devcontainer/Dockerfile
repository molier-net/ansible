FROM mcr.microsoft.com/devcontainers/base:bookworm

# Install system packages
RUN apt-get clean && rm -rf /var/lib/apt/lists/* && apt-get update && apt-get install -y \
    wget \
    unzip \
    direnv \
    pre-commit \
    git-crypt \
    age \
    yq \
    python3.11-venv \
    && rm -rf /var/lib/apt/lists/*

USER vscode

# Set up direnv hook
RUN echo 'eval "$(direnv hook bash)"' >> ~/.bashrc
RUN echo 'eval "$(direnv hook bash)"' >> ~/.bash_profile

# Copy direnv config
COPY direnv/config.toml /home/vscode/.config/direnv/config.toml

# Enable git
RUN git config --global --add safe.directory /workspaces 
