# 🌐 Deploy to Sepolia Testnet - Step by Step Guide

## Why Sepolia?
- ✅ Data persists forever (never erased)
- ✅ Free test ETH available
- ✅ Real blockchain environment
- ✅ No need to keep node running
- ✅ Share with team members easily

---

## Step 1: Get Sepolia Test ETH (5 minutes)

### Option A: Alchemy Faucet (Easiest)
1. Go to: https://sepoliafaucet.com
2. Sign in with email/Google
3. Enter your wallet address
4. Get 0.5 test ETH instantly

### Option B: Other Faucets
- https://www.alchemy.com/faucets/ethereum-sepolia
- https://faucets.chain.link/sepolia
- https://sepolia-faucet.pk910.de/

---

## Step 2: Get Infura API Key (3 minutes)

1. **Sign up at Infura:**
   - Go to: https://infura.io
   - Create free account
   - Verify email

2. **Create New Project:**
   - Click "Create New Key"
   - Select "Web3 API (Formerly Ethereum)"
   - Name it: "EPC Project Manager"

3. **Copy Your API Key:**
   - You'll see something like: `abc123def456...`
   - Copy the entire key

---

## Step 3: Configure Environment Variables

1. **Create/Edit `.env` file:**

```env
# Your wallet's private key (NEVER share this!)
PRIVATE_KEY=your_private_key_here

# Infura RPC URL
SEPOLIA_RPC_URL=https://sepolia.infura.io/v3/YOUR_INFURA_KEY

# Contract address (will be updated after deployment)
REACT_APP_CONTRACT_ADDRESS=
```

2. **Get Your Private Key from MetaMask:**
   - Open MetaMask
   - Click 3 dots → Account Details
   - Click "Show Private Key"
   - Enter password
   - Copy the key
   - **⚠️ NEVER share this with anyone!**

---

## Step 4: Deploy to Sepolia

```powershell
# Deploy the contract
npx hardhat run scripts/deploy.js --network sepolia

# Wait 1-2 minutes for deployment...
```

**Expected Output:**
```
✅ EPCProjectManager deployed to: 0x1234...abcd
```

---

## Step 5: Update React App

The deploy script automatically updates your `.env` file with the new contract address.

**Verify it:**
```powershell
Get-Content .env
```

Should show:
```
REACT_APP_CONTRACT_ADDRESS=0x1234...abcd
```

---

## Step 6: Configure MetaMask for Sepolia

1. **Open MetaMask**
2. **Click network dropdown** (top left)
3. **Enable "Show test networks":**
   - Settings → Advanced → Show test networks (ON)
4. **Select "Sepolia"** from network list
5. **Verify you have test ETH** (balance should show)

---

## Step 7: Start Your React App

```powershell
npm start
```

1. Click "Connect Wallet"
2. Make sure MetaMask is on **Sepolia** network
3. Connect your wallet
4. Start creating projects!

---

## ✅ Benefits You Get:

| Feature | Localhost | Sepolia Testnet |
|---------|-----------|-----------------|
| Data Persistence | ❌ Lost on restart | ✅ **Forever** |
| Need Node Running | ✅ Yes, always | ❌ No |
| Survives Restart | ❌ No | ✅ **Yes** |
| Share with Team | ❌ Hard | ✅ **Easy** |
| Cost | Free | Free (test ETH) |
| Speed | Very Fast | Fast enough |

---

## 🔐 Security Notes:

⚠️ **IMPORTANT:**
- **NEVER** commit your `.env` file to Git
- **NEVER** share your private key
- `.gitignore` already excludes `.env` file
- Only use test wallets with test ETH (not real money)
- This is for testing only, not production

---

## 💰 Getting More Test ETH:

If you run out of test ETH:
- Most faucets give 0.1-0.5 ETH per day
- Create multiple wallet addresses
- Join Discord communities (some give test ETH)
- Visit multiple faucets (different ones have different limits)

---

## 🐛 Troubleshooting:

**"Insufficient funds" error:**
- Get more test ETH from faucets
- Wait 24 hours and try again

**"Transaction failed":**
- Check you're on Sepolia network in MetaMask
- Verify contract address is correct
- Ensure you have enough gas (0.01 ETH minimum)

**"Contract not found":**
- Wait 1-2 minutes after deployment
- Verify network in MetaMask matches deployment network
- Check contract address in `.env` matches deployment

---

## 🎉 You're Done!

Now your data will persist forever! You can:
- ✅ Restart computer anytime
- ✅ Access from different computers
- ✅ Share with team members
- ✅ Never lose your roles/projects again

**Pro Tip:** Bookmark your contract on Etherscan:
https://sepolia.etherscan.io/address/YOUR_CONTRACT_ADDRESS

