# 🔄 Restart Guide - Start Fresh on Another Day

This guide shows you how to restart your development environment when you come back another day.

---

## 🎯 Quick Start (5 Minutes)

If you just want to get started quickly:

```bash
# Terminal 1: Start Hardhat node
npm run node

# Terminal 2: Run auto-restart script
npx hardhat run scripts/auto-restart.js --network localhost

# Terminal 3: Start React app
npm start
```

Then open browser to `http://localhost:3000` and connect wallet!

---

## 📋 Detailed Step-by-Step Guide

### ⚠️ Why You Need to Restart

When you close your computer or stop Hardhat:
- ❌ The local blockchain data is lost
- ❌ All deployed contracts are gone
- ❌ All projects and transactions disappear
- ❌ MetaMask will have old transaction history

**You need to redeploy everything!**

---

## 🚀 Complete Restart Process

### Step 1: Start Hardhat Node

**Open Terminal 1:**

```bash
cd C:\Users\mahdi\OneDrive\Desktop\website
npm run node
```

**Or:**

```bash
npx hardhat node
```

**Expected output:**
```
Started HTTP and WebSocket JSON-RPC server at http://127.0.0.1:8545/

Accounts
========
Account #0: 0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266 (10000 ETH)
Account #1: 0x70997970C51812dc3A010C7d01b50e0d17dc79C8 (10000 ETH)
...
```

✅ **Keep this terminal running!** Don't close it.

---

### Step 2: Deploy Contract

**Open Terminal 2 (New Terminal):**

```bash
cd C:\Users\mahdi\OneDrive\Desktop\website
npx hardhat run scripts/deploy.js --network localhost
```

**Expected output:**
```
✅ EPCProjectManager deployed to: 0x5FbDB2315678afecb367f032d93F642f64180aa3
```

**Copy the contract address!** You'll need it in the next step.

---

### Step 3: Update .env File

**Open `.env` file** (in the root folder) and update:

```env
REACT_APP_CONTRACT_ADDRESS=0x5FbDB2315678afecb367f032d93F642f64180aa3
```

Replace with **your actual deployed contract address** from Step 2.

**Save the file!**

---

### Step 4: Setup Test Project (Optional but Recommended)

**In Terminal 2, run:**

```bash
npx hardhat run scripts/quick-setup.js --network localhost
```

This will:
- ✅ Create a test project
- ✅ Fund it with 50 ETH
- ✅ Add a consultant
- ✅ Set up all roles

**Or skip this and create projects manually through the website.**

---

### Step 5: Reset MetaMask (Important!)

**Why?** MetaMask still has old transaction data from yesterday.

1. **Open MetaMask**
2. **Click Settings** (3 dots menu)
3. **Advanced**
4. **Scroll down to "Clear activity tab data"**
5. **Click "Clear"**

**Do this for ALL accounts** you used (Admin, Contractor, Project Manager, Consultant).

**Alternative:** Just ignore the warning in MetaMask and continue.

---

### Step 6: Start React App

**In Terminal 3 (or Terminal 2 if you're done with setup):**

```bash
npm start
```

**Expected:**
- Browser opens automatically to `http://localhost:3000`
- Or manually open: `http://localhost:3000`

---

### Step 7: Connect Wallet

1. **Click "Connect Wallet"** on the website
2. **Approve in MetaMask**
3. **Make sure you're on "Localhost 8545"** network
4. **Switch to Admin account** to start creating projects

---

## 📝 Summary Checklist

Before you start working:

- [ ] **Terminal 1:** Hardhat node running (`npm run node`)
- [ ] **Terminal 2:** Contract deployed
- [ ] **`.env` file:** Updated with new contract address
- [ ] **Terminal 3:** React app running (`npm start`)
- [ ] **MetaMask:** Reset transaction history
- [ ] **MetaMask:** Connected to Localhost 8545
- [ ] **Browser:** Open to `http://localhost:3000`

---

## 🎮 Test Accounts Reference

Keep these handy for testing:

| Role | Address | Private Key |
|------|---------|-------------|
| **Admin** | `0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266` | `0xac0974bec39a17e36ba4a6b4d238ff944bacb478cbed5efcae784d7bf4f2ff80` |
| **Contractor** | `0x70997970C51812dc3A010C7d01b50e0d17dc79C8` | `0x59c6995e998f97a5a0044966f0945389dc9e86dae88c7a8412f4603b6b78690d` |
| **Project Manager** | `0x3C44CdDdB6a900fa2b585dd299e03d12FA4293BC` | `0x5de4111afa1a4b94908f83103eb1f1706367c2e68ca870fc3fb9a804cdab365a` |
| **Consultant** | `0x90F79bf6EB2c4f870365E785982E1f101E93b906` | `0x7c852118294e51e653712a81e05800f419141751be58f605c371e15141b007a6` |

---

## ⚡ Even Faster - Auto Restart Script

Let me create a single script that does Steps 2-4 automatically:

**Save this as `scripts/auto-restart.js`** (I'll create it for you)

**Then just run:**

```bash
# After starting Hardhat node (Terminal 1)
npx hardhat run scripts/auto-restart.js --network localhost
npm start
```

**That's it!** Contract deployed, .env updated, project created, and you're ready to test!

---

## 🐛 Common Issues

### Issue 1: "Contract not found" or "Invalid address"

**Cause:** Old contract address in `.env`

**Fix:**
1. Check Terminal 2 for the new contract address
2. Update `.env` file
3. Restart React app (`Ctrl+C` then `npm start`)

---

### Issue 2: MetaMask shows "Nonce too high" error

**Cause:** MetaMask has old transaction data

**Fix:**
1. MetaMask → Settings → Advanced
2. "Clear activity tab data" → Click "Clear"
3. Or "Reset Account" for that specific account

---

### Issue 3: Website shows "Network mismatch"

**Cause:** MetaMask not on Localhost

**Fix:**
1. Click network dropdown in MetaMask
2. Select "Localhost 8545"
3. Refresh website

---

### Issue 4: Hardhat node shows old transactions

**Cause:** Node wasn't properly restarted

**Fix:**
1. Stop Hardhat node (`Ctrl+C` in Terminal 1)
2. Start it again: `npm run node`
3. Redeploy contract (Step 2)

---

## 💡 Pro Tips

### Tip 1: Save Common Commands

Create a file `start.bat` (Windows) or `start.sh` (Mac/Linux):

```bash
@echo off
echo Starting Hardhat Node...
start cmd /k "npm run node"
timeout /t 5
echo Deploying Contract...
npx hardhat run scripts/auto-restart.js --network localhost
timeout /t 2
echo Starting React App...
npm start
```

Then just double-click it to start everything!

---

### Tip 2: Keep Multiple Terminals Open

Don't close Terminal 1 (Hardhat node) - keep it running while you work.

Only Terminal 2 and 3 need to be rerun occasionally.

---

### Tip 3: Bookmark Your Local URL

Bookmark `http://localhost:3000` in your browser for quick access.

---

## 🎯 Daily Workflow

**First time (full setup):**
1. Start Hardhat node
2. Deploy contract
3. Update .env
4. Run quick-setup
5. Start React app
6. Connect wallet

**Next time (if Hardhat still running):**
1. Just run `npm start`
2. Connect wallet
3. Continue working!

**After closing everything:**
1. Start Hardhat node
2. Run auto-restart script
3. Start React app
4. Reset MetaMask
5. Connect wallet

---

## 📚 Related Guides

- **`QUICK_DEPLOY.md`** - First time setup
- **`COMPLETE_TEST_WORKFLOW.md`** - Testing payment workflow
- **`TESTING_GUIDE.md`** - Complete feature testing
- **`SETUP_GUIDE.md`** - Detailed setup instructions

---

## 🎉 You're Ready!

Once you complete these steps, you can:
- ✅ Create projects
- ✅ Request payments
- ✅ Approve payments (1 approval needed)
- ✅ Execute payments
- ✅ Complete projects

**Enjoy building!** 🚀

---

*Last Updated: After fixing payment approval to require only 1 consultant approval*
