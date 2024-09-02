# Deploy a miner node on Nesa network testnet
> Nesa is an L1 blockchain that allows developers to integrate any AI model to launch their own Dapp or blockchain rollup on its network.
>
> With its white paper, Nesa shows potential as a comprehensive blockchain platform for integrating AI models in the development of rollups and smart contracts.

## Hardware Requirement
![image](https://github.com/user-attachments/assets/fc99390f-66cf-4931-8aca-675597fa0db4)
> GPU is not necessary and you can run your miner CPU-only


## Step 1: Install Dependecies
### 1. Install dependecies
```console
sudo apt update && sudo apt upgrade -y
sudo apt install curl iptables build-essential git wget lz4 jq make gcc nano automake autoconf tmux htop nvme-cli pkg-config libssl-dev libleveldb-dev tar clang bsdmainutils ncdu unzip libleveldb-dev -y
```
### 2. Install Docker
```console
sudo apt-get update && sudo apt-get upgrade -y
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Check version
docker --version

# Give permissions to docker
sudo groupadd docker
sudo usermod -aG docker $USER
```

##  Step 2: Obtain a Hugging Face API key
1. Visit the [Hugging Face website](https://huggingface.co/).

2. Sign up or log in to your account.

3. Navigate to your [API access tokens page](https://huggingface.co/settings/tokens) under your account settings.

4. Click **“Create new token”**, head to **“Write”** tab, and generate an API key by clicking on **“Create token”** .

5. Copy the generated key to use it in your miner installation.

## Step 3: Obtain LeapWallet privatekey
Create a cosmos wallet in Leap Wallet and export your wallet private key

![Screenshot_1](https://github.com/user-attachments/assets/876ae952-fb94-4f89-800d-6ca25631ca44)

##  Step 4: Open Ports
```console
sudo ufw allow ssh
sudo ufw allow 22
sudo ufw allow 31333
sudo ufw enable
```

##  Step 5: Install and run Nesa Miner
```
bash <(curl -s https://raw.githubusercontent.com/nesaorg/bootstrap/master/bootstrap.sh)
```
* **Select a mode**: Choose **Wizardy**.
* **Choose a Moniker**: Provide a unique name for your node.
* **Node hostname**: skip & press `Enter`.
* **Node email**: skip & press `Enter`.
* **Enter Referral Code: to get bonus points**: `nesa1w8gv09dqv2fss8h7s92ye7e8afts608d9pyw65`
* **Wallet Private Key**: Enter your wallet private key for miner registration and to receive rewards.
* Finalize Configuration: Review and confirm the configuration before starting your node. The bootstrap script will provide a summary of your configuration and allow you to make changes before starting the miner.

![image](https://github.com/user-attachments/assets/69540b5a-1461-41a4-8a20-6efe4d5686f7)

##  Step 6: Useful commands

### Check container logs
```
docker logs -f orchestrator
```
```
docker logs -f mongodb
```

Check Containers: You must have 4 new containers now
```
docker ps
```

### Get node peer-id (wallet public key)
```console
cat $HOME/.nesa/identity/node_id.id
```

### Get node status url
```
PUB_KEY=$(cat $HOME/.nesa/identity/node_id.id)
echo https://node.nesa.ai/nodes/$PUB_KEY
```
![image](https://github.com/user-attachments/assets/1c33ea05-6d59-4c7e-a061-76324b2e0134)

## OptionaL: Update or Restart node
* For existing nodes that just need to update their configuration or restart their node

```
bash <(curl -s https://raw.githubusercontent.com/nesaorg/bootstrap/master/bootstrap.sh)
```

**1. select "Advanced Wizardry"**

**2. Select Yes to bootstrap it, even if it is currently running.**

* This will update your config and reboot the containers if they are running or start them if they are not.

* After this, use `cat ~/.nesa/identity/node_id.id` to check your **node_id** and make sure it is as you think it is. Check the stats at https://node.nesa.ai/

## Tokenomic:
The $NES token will be launched on the mainnet network, and 8.8% of it will be airdropped to the incentivized testnet participants.

![GMpSQF5XAAABwMI](https://github.com/user-attachments/assets/a3bb334d-a55a-41f8-9a04-a333444e04fe)
