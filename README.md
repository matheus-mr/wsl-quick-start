# wsl-quick-start

# WSL setup
wsl --install
echo "$USER ALL=(ALL:ALL) NOPASSWD: ALL" | sudo tee /etc/sudoers.d/$USER
sudo apt update && sudo apt upgrade
sudo apt-get install wget ca-certificates curl

## Git
git config --global fetch.prune true

## Docker
printf "[boot]\ncommand=\"service docker start\"\n" | sudo tee /etc/wsl.conf
sudo usermod -aG docker $USER
