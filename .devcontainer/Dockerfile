FROM mcr.microsoft.com/devcontainers/base:ubuntu-24.04

# Install basic C development tools + chezmoi
RUN apt-get update && \
    apt-get install -y \
        build-essential \
        gdb \
        valgrind \
        cmake \
        git \
        curl \
        unzip \
        zsh \
        vim \
    && curl -fsLS get.chezmoi.io | sh \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

# Optional: Install mise
COPY --from=jdxcode/mise /usr/local/bin/mise /usr/local/bin/

# Enable mise in both shells
RUN echo 'eval "$(mise activate bash)"' >> /home/vscode/.bashrc && \
    echo 'eval "$(mise activate zsh)"' >> /home/vscode/.zshrc

# Set working directory
WORKDIR /workspaces/project
