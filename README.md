# WSL quick start Ubuntu

## Install WSL
```
wsl --install
```

## No password needed for sudo
```
echo "$USER ALL=(ALL:ALL) NOPASSWD: ALL" | sudo tee /etc/sudoers.d/$USER
```

## Create download and projects directories
```
mkdir ~/Downloads & mkdir ~/Projects
```

## Update packages and repositories
```
sudo apt update && sudo apt upgrade -y
```

## Install basic packages
```
sudo apt-get install wget ca-certificates curl git unzip jq apt-transport-https software-properties-common coreutils build-essential \
build-essential libssl-dev zlib1g-dev \
libbz2-dev libreadline-dev libsqlite3-dev \
libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev -y
```

## Git/Github Config

Generate ssh keys
```
ssh-keygen -t ed25519 -C "your_email@example.com"
```

Start ssh agent
```
eval "$(ssh-agent -s)"
```

Add ssh key to agent
```
ssh-add ~/.ssh/id_ed25519
```

Copy the public key contents to clipboard and paste on github
```
cat ~/.ssh/id_ed25519.pub
```

Test connection to github (choose yes to add to known hosts)
```
ssh -T git@github.com
```

Automatically removes branches deleted from origin
```
git config --global fetch.prune true
```

## asdf installation
Clone asdf
```
git clone https://github.com/asdf-vm/asdf.git ~/.asdf --branch v0.13.1
```
Add asdf to bash
```
nano ~/.bashrc
```
```
. $HOME/.asdf/asdf.sh
. $HOME/.asdf/completions/asdf.bash
```
Reload bash config
```
source ~/.bashrc
```
Add java plugin
```
asdf plugin add java https://github.com/halcyon/asdf-java.git
```
Add python plugin
```
asdf plugin-add python
```

## Docker
Install docker
```
sudo install -m 0755 -d /etc/apt/keyrings
```
```
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
```
```
sudo chmod a+r /etc/apt/keyrings/docker.asc
```
```
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
```
sudo apt-get update -y
```
```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
```

No sudo needed for docker commands
```
sudo usermod -aG docker $USER
```
