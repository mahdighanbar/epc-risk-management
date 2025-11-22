# Quick Deploy Guide - Get Started in 5 Minutes! ⚡

The fastest way to deploy and test your smart contract locally.

## 1️⃣ Install Dependencies (30 seconds)

```bash
npm install
```

## 2️⃣ Start Local Blockchain (10 seconds)

Open a terminal and run:
```bash
npx hardhat node
```

Keep this terminal open! You'll see 20 test accounts with 10,000 ETH each.

## 3️⃣ Deploy Contract (20 seconds)

Open a **NEW terminal** and run:
```bash
npx hardhat run scripts/deploy.js --network localhost
```

You'll see output like:
```
✅ EPCProjectManager deployed to: 0x5FbDB2315678afecb367f032d93F642f64180aa3
```

## 4️⃣ Configure React App (10 seconds)

Copy the contract address and add it to `.env`:
```bash
echo "REACT_APP_CONTRACT_ADDRESS=0x5FbDB2315678afecb367f032d93F642f64180aa3" > .env
```

(Replace with your actual deployed address)

## 5️⃣ Start React App (20 seconds)

```bash
npm start
```

Browser opens automatically at `http://localhost:3000`

## 6️⃣ Connect MetaMask (1 minute)

### First time setup:

1. **Add Localhost Network to MetaMask:**
   - Open MetaMask
   - Click network dropdown → "Add Network" → "Add a network manually"
   - Enter:
     - Network Name: `Localhost 8545`
     - RPC URL: `http://127.0.0.1:8545`
     - Chain ID: `31337`
     - Currency Symbol: `ETH`

2. **Import Test Account:**
   - Copy private key from terminal running `npx hardhat node`
   - MetaMask → Account icon → Import Account
   - Paste private key

3. **Connect to Website:**
   - Click "Connect Wallet" on your website
   - Approve in MetaMask

## 🎉 Done! You're ready to test!

### What to try:
- ✅ Create a project (you're the admin)
- ✅ Add team members
- ✅ Upload documents
- ✅ Request payments
- ✅ Approve and execute payments

## 🔄 Need to Reset?

If something goes wrong:

1. Stop the local blockchain (Ctrl+C in the hardhat node terminal)
2. Delete `deployment-info.json` (if it exists)
3. Start from step 2 again

---

## Next Steps

Once everything works locally:
- 📖 Read `DEPLOYMENT_INSTRUCTIONS.md` for testnet deployment
- 🧪 Run tests: `npx hardhat test`
- 🔍 Check `contracts/README.md` to understand the architecture

**Happy Building! 🚀**
