# Complete Setup Guide 🚀

Follow these steps to get your EPC Project Manager with smart contracts up and running!

## Step 1: Install All Dependencies

First, install both React and Hardhat dependencies:

```bash
npm install
```

This will install:
- ✅ React and frontend dependencies
- ✅ Hardhat (smart contract development)
- ✅ OpenZeppelin contracts (security library)
- ✅ Ethers.js (blockchain interaction)

**Expected time:** 1-2 minutes

## Step 2: Verify Installation

Check that Hardhat is installed correctly:

```bash
npx hardhat
```

You should see Hardhat's help menu. If you see it, you're good to go!

## Step 3: Compile Your Smart Contract

```bash
npm run compile
```

or

```bash
npx hardhat compile
```

This will:
- ✅ Compile `EPCProjectManager.sol`
- ✅ Generate artifacts in `artifacts/` folder
- ✅ Create typechain files for TypeScript support

**Expected output:**
```
Compiled 1 Solidity file successfully
```

## Step 4: Run Tests (Optional but Recommended)

```bash
npm run test:contracts
```

or

```bash
npx hardhat test
```

This verifies everything works correctly before deployment.

**Expected:** All tests should pass ✅

## Step 5: Choose Your Deployment Method

### 🏠 Method A: Local Development (Easiest)

**Perfect for:** Testing, development, learning

1. **Start local blockchain** (Terminal 1):
```bash
npm run node
```

Keep this running! You'll see 20 test accounts.

2. **Deploy contract** (Terminal 2):
```bash
npm run deploy:local
```

3. **Copy the contract address** from the output

4. **Create `.env` file**:
```bash
echo "REACT_APP_CONTRACT_ADDRESS=YOUR_ADDRESS_HERE" > .env
```

5. **Start React app** (same Terminal 2):
```bash
npm start
```

6. **Configure MetaMask:**
   - Add network: `http://127.0.0.1:8545`, Chain ID: `31337`
   - Import one of the test accounts (copy private key from Terminal 1)

7. **Connect wallet** on the website

✅ **Done!** You can now test everything locally.

---

### 🌐 Method B: Sepolia Testnet (Public Testing)

**Perfect for:** Sharing with team, realistic testing

1. **Get Sepolia test ETH:**
   - Visit [sepoliafaucet.com](https://sepoliafaucet.com/)
   - Enter your wallet address
   - Wait for test ETH

2. **Create `.env` file:**
```env
PRIVATE_KEY=your_metamask_private_key
SEPOLIA_RPC_URL=https://sepolia.infura.io/v3/YOUR-PROJECT-ID
REACT_APP_CONTRACT_ADDRESS=
```

3. **Deploy to Sepolia:**
```bash
npm run deploy:sepolia
```

4. **Copy contract address** and add to `.env`:
```env
REACT_APP_CONTRACT_ADDRESS=0x...
```

5. **Start React app:**
```bash
npm start
```

6. **Connect MetaMask** (make sure you're on Sepolia network)

✅ **Done!** Your contract is now on a public testnet.

---

## Step 6: Test All Features

Once deployed and connected:

### As Admin (Deployer Account):
1. ✅ Create a project
2. ✅ Add team members (contractor, project manager, consultant)
3. ✅ Fund the project

### As Contractor:
1. ✅ Upload documents
2. ✅ Request payments

### As Consultant:
1. ✅ View documents
2. ✅ Approve payment requests

### As Project Manager:
1. ✅ Execute approved payments
2. ✅ Complete projects

## 📁 Project Structure

```
your-project/
├── contracts/              # Smart contract source code
│   ├── EPCProjectManager.sol
│   └── README.md
├── scripts/               # Deployment scripts
│   └── deploy.js
├── test/                  # Smart contract tests
│   └── EPCProjectManager.test.js
├── src/                   # React frontend
│   ├── components/
│   ├── contexts/
│   ├── contracts/        # ABIs and config
│   ├── hooks/
│   ├── pages/
│   └── utils/
├── hardhat.config.js     # Hardhat configuration
├── package.json          # Dependencies and scripts
└── .env                  # Your configuration (create this)
```

## 🎯 Quick Reference Commands

```bash
# Install dependencies
npm install

# Compile contracts
npm run compile

# Run contract tests
npm run test:contracts

# Start local blockchain
npm run node

# Deploy to local network
npm run deploy:local

# Deploy to Sepolia testnet
npm run deploy:sepolia

# Start React app
npm start

# Build for production
npm run build
```

## 🔧 Troubleshooting

### "Cannot find module 'hardhat'"
```bash
npm install
```

### "Contract not deployed"
- Make sure you've set `REACT_APP_CONTRACT_ADDRESS` in `.env`
- Restart your React app after changing `.env`

### "Network mismatch"
- Check MetaMask is on the correct network
- For local: Add network (RPC: `http://127.0.0.1:8545`, Chain ID: `31337`)

### Compilation errors
```bash
npx hardhat clean
npm run compile
```

### Need to reset local blockchain
- Stop `npx hardhat node` (Ctrl+C)
- Start it again
- Redeploy the contract

## 📚 Documentation

- **Quick Start:** `QUICK_DEPLOY.md`
- **Full Deployment Guide:** `DEPLOYMENT_INSTRUCTIONS.md`
- **Contract Details:** `contracts/README.md`
- **Integration Status:** `CONTRACT_INTEGRATION_COMPLETE.md`
- **Main README:** `README.md`

## 🎓 Learning Resources

- [Hardhat Documentation](https://hardhat.org/docs)
- [OpenZeppelin Contracts](https://docs.openzeppelin.com/contracts)
- [Ethers.js v6 Documentation](https://docs.ethers.org/v6/)
- [React Documentation](https://react.dev/)

## ⚠️ Important Notes

1. **Never commit `.env`** - It contains sensitive information
2. **Use testnets first** - Test thoroughly before mainnet
3. **Keep private keys safe** - Never share them
4. **The deployer is admin** - The account that deploys has full control
5. **Gas costs money** - Even on testnets (but test ETH is free)

## 🆘 Need Help?

1. Check the browser console (F12) for errors
2. Check the terminal running your React app
3. Review contract events on a block explorer
4. Read the relevant documentation file
5. Check that all environment variables are set correctly

---

## ✨ You're Ready!

Everything is set up and ready to go. Start with **Step 1** above and you'll be testing your smart contract in minutes!

**Recommended path for first-time users:**
1. Install dependencies
2. Compile contracts
3. Run tests
4. Deploy locally (Method A)
5. Test all features
6. Deploy to testnet (Method B) when ready

**Happy building! 🚀**
