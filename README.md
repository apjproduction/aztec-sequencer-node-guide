# 🧠 Aztec Sequencer Node Guide

A step-by-step guide for setting up and running an Aztec Sequencer Node.

---

## ⚙️ Installation Steps

### 1. Update & Install Dependencies

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install curl git wget jq docker.io docker-compose -y
```

---

### 2. Install Docker

Follow the official Docker installation guide:  
🔗 [Install Docker Engine](https://docs.docker.com/engine/install/)

Or run:

```bash
curl -fsSL https://get.docker.com | sh
```

Make sure Docker is running:

```bash
sudo systemctl enable docker
sudo systemctl start docker
```

---

### 3. Install Aztec Tools

```bash
bash -i <(curl -s https://install.aztec.network)
echo 'export PATH="$HOME/.aztec/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

---

### 4. Set Up RPC URLs

Use trusted providers:

- **Sepolia RPC** – Recommended: [Alchemy](https://www.alchemy.com/)
- **Beacon Chain RPC** – Recommended: [DRPC](https://drpc.org/)

Update `.env` or CLI values accordingly.

---

## 🛠️ Useful Commands

### ✅ Check Node Status

```bash
curl -s -X POST -H 'Content-Type: application/json' \
-d '{"jsonrpc":"2.0","method":"node_getL2Tips","params":[],"id":67}' \
http://localhost:8080 | jq -r ".result.proven.number"
```

---

### 🔐 Register as Validator

```bash
aztec add-l1-validator \
  --l1-rpc-urls <RPC_URL> \
  --private-key <YOUR_PRIVATE_KEY> \
  --attester <YOUR_ADDRESS> \
  --beacon-rpc-url <BEACON_RPC> \
  --eth-account-index 0
```

---

### 🧪 Claim Apprentice Role

Once your node is synced:

1. Go to Discord → `#operators` > `start-here`
2. Provide:
   - Your Wallet Address
   - Block Number
   - Sync Proof (from node)

---

## 📎 Resources

- Official Docs: [https://docs.aztec.network/](https://docs.aztec.network/)
- Join Discord: [Aztec Discord](https://discord.gg/aztec)

---

## 📄 License

This project is licensed under the [MIT License](LICENSE).

---

## 📦 .gitignore

A sample `.gitignore` should include:

```
node_modules/
.env
.DS_Store
*.log
__pycache__/
build/
dist/
*.swp
```

---

## 📊 Badges (Optional)

You can add these to the top of your README:

```markdown
![Stars](https://img.shields.io/github/stars/apjproduction/aztec-sequencer-node-guide?style=social)
![Forks](https://img.shields.io/github/forks/apjproduction/aztec-sequencer-node-guide?style=social)
![License](https://img.shields.io/github/license/apjproduction/aztec-sequencer-node-guide)
```

---

Made with 💻 by [@apjproduction](https://github.com/apjproduction)