# 🌅 Daily Quick Start Guide

Use this guide every time you want to work on your project.

---

## ⚡ Super Quick Start (3 Commands)

```bash
# Terminal 1: Start blockchain
npm run node

# Terminal 2: Deploy everything (wait for Terminal 1 to start first!)
npx hardhat run scripts/auto-restart.js --network localhost

# Terminal 3: Start website
npm start
```

Then:
1. Open `http://localhost:3000`
2. Connect MetaMask (use Localhost 8545 network)
3. Start testing!

---

## 📋 What Each Command Does

### Command 1: `npm run node`
- Starts local Hardhat blockchain
- Creates 20 test accounts with 10,000 ETH each
- **Keep this running!** Don't close this terminal

### Command 2: `npx hardhat run scripts/auto-restart.js --network localhost`
- Deploys smart contract
- Updates .env file automatically
- Creates a test project
- Funds it with 50 ETH
- Adds consultant
- **Only run once per session!**

### Command 3: `npm start`
- Starts React development server
- Opens browser automatically
- Website ready at `http://localhost:3000`

---

## 🎯 Complete Process

### Step 1: Open Terminal 1
```bash
cd C:\Users\mahdi\OneDrive\Desktop\website
npm run node
```

**Wait for:** "Started HTTP and WebSocket JSON-RPC server"

✅ **Leave this terminal open!**

---

### Step 2: Open Terminal 2
```bash
cd C:\Users\mahdi\OneDrive\Desktop\website
npx hardhat run scripts/auto-restart.js --network localhost
```

**Wait for:** "🎉 Auto-Restart Complete!"

This takes about 30 seconds.

---

### Step 3: Reset MetaMask (First Time Only)

For each account you used yesterday:

1. Open MetaMask
2. Click Settings (3 dots)
3. Advanced
4. "Clear activity tab data" → Click "Clear"

**Or skip this** and just ignore MetaMask warnings.

---

### Step 4: Open Terminal 3
```bash
cd C:\Users\mahdi\OneDrive\Desktop\website
npm start
```

**Browser opens automatically** to `http://localhost:3000`

---

### Step 5: Connect Wallet

1. Click "Connect Wallet" button
2. Choose MetaMask
3. Make sure you're on **"Localhost 8545"** network
4. Approve connection

---

### Step 6: Start Testing! 🎉

You now have:
- ✅ Contract deployed
- ✅ Test project created
- ✅ Project funded with 50 ETH
- ✅ All roles assigned
- ✅ Website running
- ✅ Wallet connected

**Ready to test the payment workflow!**

---

## 👥 Test Accounts

| Role | Address (first 10 chars) |
|------|--------------------------|
| Admin | `0xf39Fd6e51a...` |
| Contractor | `0x70997970C5...` |
| Project Manager | `0x3C44CdDdB6...` |
| Consultant | `0x90F79bf6EB...` |

Full addresses and private keys are in `RESTART_GUIDE.md`

---

## 🧪 Quick Test Workflow

Once everything is running:

1. **As Contractor** → Request 5 ETH payment
2. **As Consultant** → Approve it (only 1 approval needed!)
3. **As Project Manager** → Execute it
4. **Check contractor balance** → Should increase by ~5 ETH

Detailed steps: See `COMPLETE_TEST_WORKFLOW.md`

---

## ⏸️ When You're Done for the Day

### To Pause (Keep Data):
- Just close the browser
- Keep terminals running
- Everything stays active!

### To Stop (Lose Data):
1. **Ctrl+C** in Terminal 3 (React)
2. **Ctrl+C** in Terminal 1 (Hardhat)
3. Close all terminals

**⚠️ Note:** Stopping Hardhat node erases all blockchain data!

---

## 🔄 Coming Back Tomorrow?

If you stopped everything:

1. Run the 3 commands again (from top of this file)
2. Reset MetaMask
3. Continue testing!

**That's it!** Everything is scripted for you.

---

## 🐛 Common Issues

### "Contract not found"
- Did you run the auto-restart script?
- Check `.env` has the contract address
- Restart React app (Ctrl+C then `npm start`)

### "Network mismatch"
- Switch MetaMask to "Localhost 8545"
- Chain ID should be: 31337

### "Nonce too high"
- Clear MetaMask activity data
- Or reset the account in MetaMask

### "Connection refused"
- Make sure Hardhat node (Terminal 1) is running
- Check it's on `http://127.0.0.1:8545`

---

## 📚 More Information

- **`RESTART_GUIDE.md`** - Detailed restart instructions
- **`COMPLETE_TEST_WORKFLOW.md`** - Full payment workflow test
- **`TESTING_GUIDE.md`** - Complete feature testing
- **`QUICK_DEPLOY.md`** - First time setup

---

## 🎯 That's It!

You're now ready to:
- ✅ Create projects
- ✅ Request payments
- ✅ Approve payments (1 approval needed)
- ✅ Execute payments
- ✅ Test all features

**Happy coding! 🚀**

---

*Run these 3 commands and you're good to go:*
1. `npm run node`
2. `npx hardhat run scripts/auto-restart.js --network localhost`
3. `npm start`
