# Frequently Asked Questions (FAQ)

## General Questions

### What is EPC Project Manager?
EPC Project Manager is a decentralized application (DApp) for managing Engineering, Procurement, and Construction projects using blockchain technology. It provides transparent project management, secure fund management through escrow, document storage on IPFS, and multi-signature payment approvals.

### Why use blockchain for project management?
Blockchain provides:
- **Transparency**: All transactions are recorded publicly
- **Immutability**: Records cannot be altered or deleted
- **Security**: Cryptographic security and smart contracts
- **Trust**: No single point of control
- **Automation**: Smart contracts execute automatically
- **Auditability**: Complete history of all actions

### Do I need cryptocurrency to use this app?
Yes, you need cryptocurrency (ETH, MATIC, etc.) for:
- Deploying smart contracts
- Creating projects
- Uploading documents
- Requesting/approving payments
- All blockchain transactions

For testing, you can use free test tokens from faucets.

### Is this app free to use?
The application code is free and open-source (MIT License). However, you'll pay:
- **Gas fees**: For blockchain transactions
- **IPFS storage**: Some IPFS services are free, some require payment
- No subscription or platform fees

## Technical Questions

### What blockchain networks are supported?
- Ethereum Mainnet
- Ethereum Testnets (Goerli, Sepolia)
- Polygon Mainnet
- Polygon Mumbai Testnet
- Localhost (for development)

### What is IPFS?
IPFS (InterPlanetary File System) is a decentralized storage network. Documents uploaded to IPFS:
- Cannot be deleted or modified
- Are accessible globally
- Don't rely on centralized servers
- Are identified by unique hashes

### How do I get test ETH?
Use these faucets:
- **Sepolia**: https://sepoliafaucet.com
- **Goerli**: https://goerlifaucet.com
- **Mumbai**: https://faucet.polygon.technology

### Can I use this without MetaMask?
MetaMask is recommended, but you can use any Web3-compatible wallet that supports:
- Browser injection (window.ethereum)
- WalletConnect
- Hardware wallets (Ledger, Trezor)

### What programming languages are used?
- **Smart Contracts**: Solidity 0.8.20
- **Frontend**: React 18 with JavaScript
- **Styling**: Tailwind CSS
- **Web3**: ethers.js 6.9.0

## Setup and Installation

### How do I install the application?
```bash
# Clone repository
git clone <repository-url>

# Install dependencies
npm install

# Configure environment
cp .env.example .env
# Edit .env with your contract address

# Start application
npm start
```

See [QUICK_START.md](QUICK_START.md) for detailed instructions.

### Why isn't my wallet connecting?
Common solutions:
1. Install MetaMask browser extension
2. Unlock your MetaMask wallet
3. Refresh the page
4. Check you're on the correct network
5. Clear browser cache
6. Disable conflicting extensions

### How do I deploy the smart contract?
See [DEPLOYMENT_GUIDE.md](DEPLOYMENT_GUIDE.md) for complete instructions. Quick version:
1. Use Remix IDE (easiest) or Hardhat
2. Deploy to testnet first
3. Copy contract address
4. Add to .env file

### Where do I put the contract address?
In the `.env` file in your project root:
```
REACT_APP_CONTRACT_ADDRESS=0xYourContractAddressHere
```

## Usage Questions

### How do I create a project?
1. You must have the **Admin** role
2. Go to "Projects" page
3. Click "Create Project"
4. Fill in:
   - Project name
   - Contractor address
   - Project manager address
   - Budget in ETH
5. Confirm transaction in MetaMask

### How does the payment workflow work?
```
1. Contractor requests payment
2. Consultants approve (2 required)
3. Project manager executes
4. Funds released from escrow
```

### How do I upload a document?
1. Upload your file to IPFS using:
   - Pinata.cloud
   - Web3.Storage
   - Infura IPFS
2. Copy the IPFS hash (starts with "Qm")
3. Go to "Documents" page
4. Click "Upload Document"
5. Paste IPFS hash and add description
6. Confirm transaction

### Can I delete a document?
No. Documents on IPFS and blockchain records are permanent. This ensures data integrity and prevents tampering.

### How do I check my role?
Go to the "Team" page to see your current role and permissions.

### What can each role do?
- **Admin** 👑: Everything (create projects, assign roles)
- **Project Manager** 📋: Execute payments, complete projects
- **Contractor** 🔨: Upload documents, request payments
- **Consultant** ✅: Approve payments, view documents
- **Viewer** 👁️: View documents only

### How many approvals are needed for payments?
By default, **2 consultant approvals** are required before a payment can be executed.

## Troubleshooting

### Transaction failed - what now?
Common causes:
1. **Insufficient gas**: Increase gas limit
2. **Wrong role**: You lack permission
3. **Invalid address**: Check recipient address
4. **Contract error**: Check console for details
5. **Network issues**: Try again later

### Why is gas so expensive?
Gas costs depend on:
- Network congestion
- Transaction complexity
- Selected blockchain (Polygon is cheaper than Ethereum)

Tips to reduce costs:
- Use Polygon instead of Ethereum
- Transact during off-peak hours
- Batch operations when possible
- Use testnets for practice

### My project isn't showing up
1. Wait for blockchain confirmation (can take minutes)
2. Refresh the page
3. Check you're on the correct network
4. Verify contract address in settings

### IPFS document won't load
1. Try a different IPFS gateway
2. Check the IPFS hash is correct
3. Wait - IPFS can be slow sometimes
4. Verify file was uploaded successfully

### "Contract not found" error
1. Check `.env` has correct contract address
2. Verify you deployed the contract
3. Ensure you're on the correct network
4. Restart development server after .env changes

### Numbers show as very large
This happens with Wei conversions. The app should automatically format ETH amounts. If not:
- 1 ETH = 1,000,000,000,000,000,000 Wei
- Use ethers.formatEther() for display

## Security Questions

### Is this application secure?
The application uses:
- Audited OpenZeppelin contracts
- Role-based access control
- Multi-signature approvals
- Secure Web3 connections

However:
- Always test on testnet first
- Never share private keys
- Verify all transactions
- Consider professional audit for production

### Can someone steal funds?
Funds are protected by:
- Smart contract access control
- Multi-signature requirements
- Escrow mechanism
- Your wallet's private key

Keep your private key secure!

### What if I lose my private key?
**You permanently lose access.** There is no password reset or recovery. Always:
- Backup your seed phrase
- Store it securely offline
- Never share it with anyone

### Are transactions reversible?
No. Blockchain transactions are permanent and cannot be reversed. Always:
- Double-check amounts
- Verify recipient addresses
- Confirm transaction details

### Is my data private?
No. Blockchain data is public:
- All transactions are visible
- Wallet addresses are public
- IPFS documents are accessible by anyone
- Contract data can be read by anyone

Do not store sensitive personal information.

## Cost Questions

### How much does it cost to use?
**Variable costs (gas fees):**
- Create project: 0.01-0.05 ETH
- Upload document: 0.005-0.02 ETH
- Request payment: 0.003-0.01 ETH
- Approve payment: 0.003-0.01 ETH
- Execute payment: 0.005-0.02 ETH

Actual costs vary by network and congestion.

**Fixed costs:**
- Application: Free (open source)
- IPFS storage: Free to ~$5/month
- Domain/hosting: $0-$20/month

### Can I use this on Polygon to save money?
Yes! Polygon transactions cost a fraction of Ethereum:
- Typical transaction: $0.001-0.01
- Much faster confirmation
- Same functionality

Deploy your contract to Polygon Mumbai (testnet) or Polygon Mainnet.

### Do I pay for viewing data?
No. Reading data from the blockchain is free. You only pay gas for:
- Creating/modifying data
- Sending transactions
- Deploying contracts

## Features Questions

### Can I use this for multiple projects?
Yes! The admin can create unlimited projects. Each project:
- Has its own budget
- Has its own team members
- Maintains separate escrow
- Tracks independent payments

### Can I add more consultants?
Yes! Admins and project managers can add consultants to projects using the "Team" page.

### Can project details be changed?
No. Once created, project details are immutable. This ensures:
- Transparency
- Trust
- Audit trail

Plan carefully before creating projects.

### Is there a mobile app?
Not yet, but the web application is fully responsive and works on mobile browsers with MetaMask mobile app.

### Can I export data?
Currently, no built-in export. However:
- All data is on public blockchain
- You can query blockchain directly
- Transaction hashes can be viewed on block explorers
- Future versions may add export features

## Development Questions

### Can I modify the code?
Yes! The code is open source (MIT License). You can:
- Fork the repository
- Modify for your needs
- Deploy your own instance
- Contribute improvements

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

### How do I add a new feature?
1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

### Can I use this commercially?
Yes, the MIT License allows commercial use. You can:
- Use in production
- Charge users
- Modify and resell
- Use in proprietary projects

Just maintain the license notice.

### How do I report bugs?
Open an issue on GitHub with:
- Description of the bug
- Steps to reproduce
- Expected vs actual behavior
- Screenshots (if applicable)
- Browser/wallet versions

## Support Questions

### Where can I get help?
- **Documentation**: README.md, USER_GUIDE.md
- **GitHub Issues**: Report bugs or ask questions
- **Discussions**: GitHub Discussions for general questions
- **Community**: Discord/Telegram (if available)

### How do I request a feature?
Open a GitHub issue with:
- Feature description
- Use case/motivation
- Potential implementation approach
- Willingness to contribute

### Is there professional support?
Not currently. This is an open-source project maintained by volunteers. However:
- Community support through GitHub
- Documentation is comprehensive
- Code is well-commented

### Can I hire someone to help?
Yes, you can:
- Hire freelance blockchain developers
- Contact Web3 development agencies
- Post on blockchain developer job boards

---

## Still Have Questions?

- Check the [README.md](README.md) for overview
- Read the [USER_GUIDE.md](USER_GUIDE.md) for detailed instructions
- Review the [DEPLOYMENT_GUIDE.md](DEPLOYMENT_GUIDE.md) for setup help
- Open an issue on GitHub
- Join community discussions

---

**Last Updated**: 2024-01-XX
