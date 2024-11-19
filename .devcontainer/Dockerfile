FROM mcr.microsoft.com/devcontainers/base:ubuntu-24.04

RUN <<-EOF
set -e
apt-get update
apt-get install -y curl
apt-get clean
rm -r /var/lib/apt/lists/*
EOF

USER vscode

RUN <<-EOF
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash

echo "export NVM_DIR=\"\$HOME/.nvm\"" >> ~/.bashrc

echo "[ -s \"\$NVM_DIR/nvm.sh\" ] && \. \"\$NVM_DIR/nvm.sh\"" >> ~/.bashrc
echo "[ -s \"\$NVM_DIR/bash_completion\" ] && \. \"\$NVM_DIR/bash_completion\"" >> ~/.bashrc

export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"

nvm install 14.21.3

npm install -g meteor@2.16.0
npm install -g yarn@1.22.18
EOF