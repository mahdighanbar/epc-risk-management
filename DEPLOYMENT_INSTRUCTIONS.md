# Smart Contract Deployment Instructions

This guide will walk you through deploying your EPC Project Manager smart contracts and connecting them to your React website.

## Prerequisites

✅ Node.js installed (v16 or higher)
✅ MetaMask wallet with test ETH
✅ Basic understanding of blockchain and smart contracts

## Step 1: Install Dependencies

```bash
npm install
```

This will install all required packages including:
- Hardhat (development environment)
- OpenZeppelin contracts
- Ethers.js (blockchain interaction library)

## Step 2: Set Up Environment Variables

1. Copy the example environment file:
```bash
cp .env.example .env
```

2. Edit `.env` and add your configuration:
```env
# For deploying to testnets
PRIVATE_KEY=your_wallet_private_key_here
SEPOLIA_RPC_URL=https://sepolia.infura.io/v3/YOUR-PROJECT-ID
ETHERSCAN_API_KEY=your_etherscan_api_key

# After deployment, add this:
REACT_APP_CONTRACT_ADDRESS=deployed_contract_address_here
```

⚠️ **Security Warning**: Never commit your `.env` file or share your private key!

## Step 3: Choose Your Deployment Network

### Option A: Local Development (Recommended for Testing)

**Best for:** Initial testing and development

1. Start a local blockchain:
```bash
npx hardhat node
```

2. In a new terminal, deploy:
```bash
npx hardhat run scripts/deploy.js --network localhost
```

3. Copy the contract address from the output and add it to `.env`:
```env
REACT_APP_CONTRACT_ADDRESS=0x5FbDB2315678afecb367f032d93F642f64180aa3
```

**Advantages:**
- ✅ Free (no gas costs)
- ✅ Fast transactions
- ✅ Full control
- ✅ Easy testing and debugging

### Option B: Sepolia Testnet (Recommended for Public Testing)

**Best for:** Testing with a public testnet before mainnet

1. Get Sepolia test ETH:
   - Visit [Sepolia Faucet](https://sepoliafaucet.com/)
   - Or [Alchemy Sepolia Faucet](https://sepoliafaucet.com/)
   - Enter your wallet address

2. Configure your `.env` with Sepolia RPC URL and private key

3. Deploy to Sepolia:
```bash
npx hardhat run scripts/deploy.js --network sepolia
```

4. Verify the contract on Etherscan (optional but recommended):
```bash
npx hardhat verify --network sepolia YOUR_CONTRACT_ADDRESS
```

**Advantages:**
- ✅ Public testnet (real blockchain environment)
- ✅ Can share with others
- ✅ Verifiable on Etherscan
- ✅ Free test ETH available

### Option C: Other Networks

The project supports:
- **Goerli Testnet** (being deprecated)
- **Mumbai Testnet** (Polygon)
- **Mainnet** (requires real ETH - NOT recommended initially)

## Step 4: Understand the Deployment Output

After deployment, you'll see output like this:

```
🚀 Starting deployment...
==================================================
📝 Deploying contracts with account: 0x...
💰 Account balance: 1.5 ETH
==================================================

📦 Deploying EPCProjectManager...
✅ EPCProjectManager deployed to: 0x5FbDB2315678afecb367f032d93F642f64180aa3

📋 Sub-contract addresses:
   DocumentManager: 0xe7f1725E7734CE288F8367e1Bb143E90bb3F0512
   EscrowManager: 0x9fE46736679d2D9a65F0992F2272dE9f3c7fa6e0
   PaymentManager: 0xCf7Ed3AccA5a467e9e704C703E8D87F634fB0Fc9

👑 Contract admin: 0x...
```

**Important addresses:**
- **EPCProjectManager**: This is your main contract address - add this to `.env`
- **Sub-contracts**: Automatically deployed and managed by the main contract

## Step 5: Configure Your React Application

1. Add the contract address to `.env`:
```env
REACT_APP_CONTRACT_ADDRESS=0x5FbDB2315678afecb367f032d93F642f64180aa3
```

2. Restart your React development server:
```bash
npm start
```

3. Connect MetaMask to the same network where you deployed

## Step 6: Test the Integration

1. Open your browser to `http://localhost:3000`
2. Click "Connect Wallet"
3. Connect with the same account you used for deployment (this account is the admin)
4. Try creating a test project
5. Test document uploads, payments, etc.

## Troubleshooting

### "Network mismatch" error
- Make sure MetaMask is connected to the same network where you deployed
- For localhost: Add network in MetaMask (RPC: http://127.0.0.1:8545, Chain ID: 31337)

### "Contract not deployed" error
- Check that `REACT_APP_CONTRACT_ADDRESS` is correctly set in `.env`
- Restart your React app after changing `.env`

### "Insufficient funds" error
- Make sure your wallet has enough ETH for gas fees
- For localhost: Use one of the test accounts provided by `npx hardhat node`

### Transaction fails
- Check that you're using the correct role (admin, contractor, etc.)
- Verify the contract has been properly deployed

## Network Configuration Quick Reference

| Network | Chain ID | RPC URL | Faucet |
|---------|----------|---------|--------|
| Localhost | 31337 | http://127.0.0.1:8545 | N/A (test accounts) |
| Sepolia | 11155111 | Infura/Alchemy | [sepoliafaucet.com](https://sepoliafaucet.com) |
| Goerli | 5 | Infura/Alchemy | [goerlifaucet.com](https://goerlifaucet.com) |
| Mumbai | 80001 | polygon-rpc | [faucet.polygon.technology](https://faucet.polygon.technology) |

## Next Steps

After successful deployment:

1. ✅ Test all features thoroughly
2. ✅ Create test projects with different roles
3. ✅ Test document uploads
4. ✅ Test payment approval workflow
5. ✅ Consider security audit before mainnet deployment
6. ✅ Document your deployment addresses

## Additional Resources

- [Hardhat Documentation](https://hardhat.org/docs)
- [OpenZeppelin Contracts](https://docs.openzeppelin.com/contracts)
- [Ethers.js Documentation](https://docs.ethers.org/)
- [MetaMask Documentation](https://docs.metamask.io/)

## Need Help?

- Check the console logs in your browser (F12)
- Check the terminal running your React app
- Review the contract events on a block explorer
- Consult the project README.md

---

**Remember:** Always test thoroughly on testnets before deploying to mainnet!
