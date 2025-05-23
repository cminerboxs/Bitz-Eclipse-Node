# Guide to Bitz Miner CLI on Eclipse

## What is Bitz?
- The first ePOW commodity token that anyone can mine on Eclipse.
- 5M max supply.
- NOT pre-mined + ZERO team/insider allocations.
- Token address: https://eclipsescan.xyz/token/64mggk2nXg6vHC1qCdsZdEFzd5QGN4id54Vbho4PswCF

---

# Setup Guide
## Presequities
- Eclipse wallet (.eg `okx wallet`) funded with `0.001 ETH`
- A minimal CPU system or VPS, [Guide to buy and setup a VPS](https://x.com/cminerbox/status/1924469919103480251?s=46&t=NgAwg5Rl2WrF88epuFrfSQ).
- Linux Ubuntu Terminal
- Windows users: Must install Linux Ubuntu Terminal using WSL. 

---

## Install Dependecies
**1. Install Packages**
```bash
sudo apt-get update && sudo apt-get upgrade -y

sudo apt install screen curl nano  -y
```
**2. Install Rust**
```bash
 curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```
* When Prompted, Enter `1` and wait unti installation compelete.
```bash
source $HOME/.cargo/env
```
**3. Install Solana CLI:**
```bash
curl --proto '=https' --tlsv1.2 -sSfL https://solana-install.solana.workers.dev | bash
```
* Close and reopen your Terminal.
```
solana --version
```
* If you get `solana: command not found` RUN :
```bash
echo 'export PATH="/root/.local/share/solana/install/active_release/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```
```
solana --version
```

**4. Switch RPC**
```bash
solana config set --url https://bitz-000.eclipserpc.xyz/
```
---

## Wallet CLI
### 1. Create a CLI wallet
```bash
solana-keygen new
```
* Skip by pressing `Enter`.
* Save your Seed-Phrase & Public-Key
* `Public-Key`: Is your node **Eclipse wallet address**.

### 2. Export `Private-key`

1- Find Keypair path:
```bash
solana config get
```
* It gives your Keypair path like this: `~/.config/solana/id.json`

2- Export `Private-key`:
```bash
cat ~/.config/solana/id.json
```
* The exported array is your `Private-Key`, Save it.

### 3. Import and Fund Node Wallet
* Import `Private-Key` into your `OKX wallet` wallet.
* Fund it with `0.001 ETH` on `Eclipse` Network,  Go to Bridge $ETH to Eclipse (https://app.eclipse.xyz/bridge)
* You need 0.001 $ETH on Eclipse to start mining
* So send $ETH to your public key

---

## Install Bitz
```bash
cargo install bitz
```

---

## Run Bitz Miner
### 1. Open a screen
By opening a screen, you can run any process in the background, so it won't get terminated if you closed your VPS. (Windows users must keep their terminal open)
```bash
screen -S bitz
```

### 2. Start Miner
```bash
bitz collect
```

![image](https://github.com/user-attachments/assets/7c526a4b-07da-4ad5-889f-17674761b5e7)

* Your Miner Node is Running successfully now.
* Adjust the `-c` flag based on your device cores for your Bitz miner. Stop the node with `Ctrl+C`, then replace your `8` with your system `cores` and enter the following command:
```bash
bitz collect --cores 8
```
* minimize screen: `Ctrl+A+D`
* Check your hashpower `bitz benchmark -c 8`
* return screen: `screen -r bitz`
* stop the node while in screen: `Ctrl+C`
* screen lists: `screen -ls`
* terminate and kill screen: `screen -XS bitz quit` (if you had multiple screens in list, replace `bitz` with `id` of screen.

---

### Usefull Commands
* You have to enter these out of the screen session

**Check account info:**
```bash
bitz account
```

**Claim Bitz to your Node Wallet:**
```bash
bitz claim
```

**All Commands List:**
```bash
bitz -h
```
### Getting Help
[![Twitter](https://img.shields.io/badge/Twitter-%231DA1F2.svg?style=for-the-badge&logo=Twitter&logoColor=white)](https://x.com/cminerbox)
[![Telegram](https://img.shields.io/badge/Telegram-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white)](https://t.me/cminerboxs)
[![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white)](https://github.com/cminerboxs)
[![Direct Contact](https://img.shields.io/badge/Telegram-Direct%20Contact-green?style=for-the-badge&logo=telegram)](https://t.me/cminerbox)
