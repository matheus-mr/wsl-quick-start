# wsl-quick-start

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
sudo apt-get install wget ca-certificates curl git unzip jq coreutils build-essential \
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
No sudo needed for docker commands
```
sudo usermod -aG docker $USER
```
