FROM mcr.microsoft.com/devcontainers/base:ubuntu-24.04

SHELL ["/bin/bash", "-c"]

RUN <<-EOF
set -e
apt-get update
apt-get install -y g++ build-essential git curl
apt-get clean
rm -r /var/lib/apt/lists/*
EOF

USER vscode

RUN <<-EOF
set -e

curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash

export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"

nvm install 14.21.3
corepack enable
npm install -g meteor@2.16.0

mkdir -p /home/vscode/miniconda3
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O /home/vscode/miniconda3/miniconda.sh
bash /home/vscode/miniconda3/miniconda.sh -b -u -p /home/vscode/miniconda3
rm /home/vscode/miniconda3/miniconda.sh

source /home/vscode/miniconda3/bin/activate
conda init --all
conda create -n py310 python=3.10

echo "conda activate py310" >> /home/vscode/.bashrc

EOF