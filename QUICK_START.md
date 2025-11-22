# Quick Start Guide - EPC Project Manager

Get up and running in 5 minutes!

## 🚀 Quick Setup

### Step 1: Install Dependencies
```bash
npm install
```

### Step 2: Configure Environment
```bash
# Copy the example environment file
cp .env.example .env

# Edit .env and add your contract address
# REACT_APP_CONTRACT_ADDRESS=0xYourContractAddressHere
```

### Step 3: Start Development Server
```bash
npm start
```

The application will open at http://localhost:3000

## 📝 Before You Start

### Deploy Your Smart Contract First

1. **Option A: Using Remix IDE (Easiest)**
   - Go to https://remix.ethereum.org
   - Create a new file `EPCProjectManager.sol`
   - Paste your smart contract code
   - Compile with Solidity 0.8.20
   - Deploy to your chosen network (Sepolia testnet recommended)
   - Copy the deployed contract address

2. **Option B: Using Hardhat**
   - See DEPLOYMENT_GUIDE.md for detailed instructions

### Get Test Tokens

For testing, get free tokens from faucets:
- **Sepolia ETH**: https://sepoliafaucet.com
- **Goerli ETH**: https://goerlifaucet.com  
- **Mumbai MATIC**: https://faucet.polygon.technology

### Install MetaMask

1. Install MetaMask browser extension
2. Create or import a wallet
3. Switch to your chosen testnet
4. Add test tokens from faucets

## 🎯 First Steps After Launch

### 1. Connect Your Wallet
- Click "Connect Wallet" in the top right
- Approve the connection in MetaMask

### 2. Create Your First Project (Admin Only)
- Navigate to "Projects" page
- Click "Create Project"
- Fill in project details
- Confirm transaction

### 3. Fund the Project
- Click "Fund Project" on your created project
- Enter amount (e.g., 0.1 ETH)
- Confirm transaction

### 4. Try Other Features
- Upload a document (need IPFS hash)
- Request a payment (as contractor)
- Approve payments (as consultant)

## 📚 Key Files

```
├── src/
│   ├── App.js                 # Main application
│   ├── contexts/
│   │   └── Web3Context.js     # Web3 connection logic
│   ├── pages/
│   │   ├── Dashboard.js       # Overview page
│   │   ├── Projects.js        # Project management
│   │   ├── Documents.js       # Document management
│   │   ├── Payments.js        # Payment workflow
│   │   ├── Team.js            # Role management
│   │   └── Settings.js        # App settings
│   └── contracts/
│       └── config.js          # Contract ABIs and config
├── .env                       # Your configuration (create this!)
└── README.md                  # Full documentation
```

## 🎨 Features Overview

### Dashboard
- Project statistics
- Recent activity
- Quick actions

### Projects
- Create new projects
- View project details
- Fund projects with escrow
- Complete projects

### Documents
- Upload to IPFS
- View document history
- Access control by role

### Payments
- Request payments
- Multi-signature approval (2 consultants)
- Execute approved payments

### Team
- View role hierarchy
- Add consultants to projects
- Understand permissions

### Settings
- Network switching
- Contract information
- Wallet details

## 🔑 User Roles

- **👑 Admin**: Create projects, full control
- **📋 Project Manager**: Execute payments, complete projects
- **🔨 Contractor**: Upload documents, request payments
- **✅ Consultant**: Approve payment requests
- **👁️ Viewer**: View documents only

## 🐛 Troubleshooting

### "Cannot connect wallet"
- Install MetaMask extension
- Unlock your wallet
- Refresh the page

### "Contract not configured"
- Make sure `.env` file exists
- Add `REACT_APP_CONTRACT_ADDRESS=0x...`
- Restart development server

### "Transaction failed"
- Check you have enough gas
- Verify you have the correct role
- Ensure contract address is correct

### "Module not found"
- Run `npm install` again
- Clear node_modules: `rm -rf node_modules && npm install`

## 📖 Documentation

- **README.md**: Complete project documentation
- **DEPLOYMENT_GUIDE.md**: Detailed deployment instructions
- **USER_GUIDE.md**: End-user manual
- **Smart Contract**: See your Solidity file for contract details

## 💡 Tips

1. **Always test on testnet first** before using real money
2. **Save your contract address** - you'll need it!
3. **Backup your wallet** seed phrase securely
4. **Check gas prices** before transactions
5. **Use IPFS services** like Pinata for document uploads

## 🌟 Next Steps

1. ✅ Deploy smart contract
2. ✅ Configure .env file
3. ✅ Start application
4. ⬜ Connect wallet
5. ⬜ Create first project
6. ⬜ Test all features
7. ⬜ Deploy to production

## 📞 Need Help?

- Check the FAQ in USER_GUIDE.md
- Review DEPLOYMENT_GUIDE.md for setup issues
- Open an issue on GitHub
- Check console for error messages

## 🎉 You're Ready!

Your EPC Project Manager is now set up and ready to use. Start by connecting your wallet and exploring the features!

Happy building! 🏗️✨
