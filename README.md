# nesa-miner
## Hardware Requirement
![Screenshot_1](https://github.com/user-attachments/assets/4c32d071-4969-434a-8d35-2ba8a0fdc0b4)

## Install Dependecies
### Install packages
```console
sudo apt install jq curl
```
### Install Docker
```console
sudo apt update -y && sudo apt upgrade -y
for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done

sudo apt-get update
sudo apt-get install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update -y && sudo apt upgrade -y

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
docker --version

# Give permissions to docker
sudo groupadd docker
sudo usermod -aG docker $USER

# Test Docker
sudo docker run hello-world
```

## Obtain a Hugging Face API key
1. Visit the [Hugging Face website](https://huggingface.co/).

2. Sign up or log in to your account.

3. Navigate to your [API access tokens page](https://huggingface.co/settings/tokens) under your account settings.

4. Click **“Create new token”**, head to **“Write”** tab, and generate an API key by clicking on **“Create token”** .

5. Copy the generated key to use it in your miner installation.

### Get node peer-id (wallet public key)
```console
cat $HOME/.nesa/identity/node_id.id
```
