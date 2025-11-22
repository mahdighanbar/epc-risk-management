# EPC Project Manager - User Guide

Welcome to the EPC Project Manager! This guide will help you understand how to use the application effectively.

## Table of Contents
1. [Getting Started](#getting-started)
2. [Dashboard](#dashboard)
3. [Projects](#projects)
4. [Documents](#documents)
5. [Payments](#payments)
6. [Team Management](#team-management)
7. [Settings](#settings)
8. [FAQ](#faq)

## Getting Started

### Prerequisites
- A Web3 wallet (MetaMask recommended)
- Some cryptocurrency for gas fees (ETH, MATIC, etc.)
- Permission/role assigned by the project administrator

### Connecting Your Wallet

1. Click the "Connect Wallet" button in the top right corner
2. MetaMask will prompt you to connect
3. Select the account you want to use
4. Approve the connection

Once connected, you'll see your wallet address and the current network displayed in the header.

### Understanding Your Role

Your role determines what actions you can perform:

- **👑 Admin**: Full system access
- **📋 Project Manager**: Execute payments, complete projects
- **🔨 Contractor**: Upload documents, request payments
- **✅ Consultant**: Approve payment requests
- **👁️ Viewer**: View documents only

Check the "Team" page to see your current role and permissions.

## Dashboard

The Dashboard provides an overview of your projects and activities.

### Key Metrics
- **Total Projects**: All projects in the system
- **Active Projects**: Currently ongoing projects
- **Documents**: Total uploaded documents
- **Pending Payments**: Payment requests awaiting approval

### Quick Actions
Use the quick action cards to:
- Create a new project
- Upload a document
- Request a payment

### Recent Activity
View the latest updates and transactions related to your projects.

## Projects

Manage your EPC (Engineering, Procurement, and Construction) projects.

### Creating a Project (Admin Only)

1. Click "Create Project" button
2. Fill in the project details:
   - **Project Name**: Give your project a descriptive name
   - **Contractor Address**: Ethereum address of the contractor
   - **Project Manager Address**: Ethereum address of the project manager
   - **Budget**: Total project budget in ETH
3. Click "Create" to submit the transaction
4. Confirm the transaction in MetaMask
5. Wait for blockchain confirmation

### Viewing Projects

Each project card displays:
- Project name and status (Active/Completed)
- Contractor and project manager addresses
- Budget and current balance
- Start date

### Funding a Project

1. Click "Fund Project" on any project card
2. Enter the amount in ETH
3. Confirm the transaction in MetaMask
4. Funds are held in escrow until payments are executed

### Completing a Project (Project Manager Only)

1. Click "Complete Project" on an active project
2. Confirm the action
3. The project status changes to "Completed"

## Documents

Manage project documents stored on IPFS (InterPlanetary File System).

### Uploading Documents (Contractor/Uploader Role)

1. Click "Upload Document" button
2. First, upload your file to IPFS using:
   - [Pinata](https://pinata.cloud)
   - [Infura IPFS](https://infura.io/product/ipfs)
   - [Web3.Storage](https://web3.storage)
3. Copy the IPFS hash (starts with "Qm...")
4. Paste the hash in the "IPFS Hash" field
5. Add a description of the document
6. Click "Upload" and confirm the transaction

### Viewing Documents

1. Browse all uploaded documents
2. Each card shows:
   - Document ID
   - Description
   - IPFS hash
   - Uploader address
   - Upload date
3. Click "View on IPFS" to open the document

### Why IPFS?

IPFS provides:
- **Permanent storage**: Documents can't be deleted or modified
- **Decentralization**: No single point of failure
- **Verification**: Hash ensures document authenticity
- **Accessibility**: Available globally through gateways

## Payments

Manage payment requests with multi-signature approval workflow.

### Requesting Payment (Contractor Role)

1. Click "Request Payment" button
2. Fill in the details:
   - **Recipient Address**: Where funds should be sent
   - **Amount**: Payment amount in ETH
   - **Description**: Purpose of the payment
3. Click "Request" and confirm the transaction
4. Wait for consultants to approve

### Approving Payments (Consultant Role)

1. View pending payment requests
2. Review the details carefully:
   - Recipient
   - Amount
   - Description
   - Current approvals
3. Click "Approve" if the payment is legitimate
4. Confirm the transaction in MetaMask

### Executing Payments (Project Manager Role)

1. Wait until required approvals are reached
2. Payment status changes to "Ready to Execute"
3. Click "Execute" button
4. Confirm the transaction
5. Funds are released from escrow to the recipient

### Payment Workflow

```
Request → Approve (x2) → Execute → Funds Released
```

The default requires 2 consultant approvals before execution.

## Team Management

Manage roles and permissions for your project team.

### Understanding Roles

#### Admin (👑)
- Create and manage all projects
- Assign project managers and contractors
- Add consultants to any project
- Full system control

#### Project Manager (📋)
- Execute approved payments
- Complete projects
- Add consultants to their projects
- View project documents

#### Contractor (🔨)
- Upload project documents
- Request payments
- View project details

#### Consultant (✅)
- Approve payment requests
- View project documents
- Review project progress

#### Viewer (👁️)
- View project documents
- Read-only access

### Adding a Consultant (Admin/Project Manager)

1. Click "Add Consultant" button
2. Enter the project ID
3. Enter the consultant's wallet address
4. Click "Add" and confirm the transaction
5. The consultant can now approve payments for that project

### Best Practices

- Assign roles based on trust and responsibility
- Use multiple consultants for important projects
- Regularly review team members and their access
- Remove access when team members leave the project

## Settings

Configure your application preferences and view system information.

### Wallet Information

- View your connected wallet address
- Copy address to clipboard
- See current network

### Contract Information

- View the smart contract address
- Verify contract connection status
- Copy contract address for verification

### Network Selection

Switch between different blockchain networks:
- **Mainnet**: Production environment (real money)
- **Testnet**: Testing environment (free test tokens)
- **Localhost**: Local development

Click on any network card to switch (MetaMask will prompt you).

### Application Info

View version, build information, and technical details.

### Resources

Access helpful documentation links:
- Solidity documentation
- ethers.js documentation
- IPFS documentation

## FAQ

### How do I get test ETH?

For testnets, use faucets:
- **Sepolia**: https://sepoliafaucet.com
- **Goerli**: https://goerlifaucet.com
- **Mumbai**: https://faucet.polygon.technology

### Why is my transaction failing?

Common reasons:
- Insufficient gas fees
- Lack of required role/permission
- Incorrect contract address
- Network congestion

### How do I upload files to IPFS?

1. Create an account on Pinata or Web3.Storage
2. Upload your file through their web interface
3. Copy the IPFS hash (CID)
4. Use this hash in the document upload form

### Can I change project details after creation?

Currently, projects are immutable once created. This ensures transparency and prevents tampering. Plan carefully before creating a project.

### What happens to funds in escrow?

Funds deposited to a project remain in escrow until:
- A payment request is approved and executed
- The payment is released to the specified recipient
- Funds can only be released through the proper approval workflow

### How secure is this system?

The system uses:
- OpenZeppelin's audited smart contracts
- Multi-signature approval for payments
- Role-based access control
- Immutable blockchain records
- Decentralized document storage

### Can I use this on mobile?

Yes! The application is responsive and works on mobile browsers with MetaMask mobile app or WalletConnect-compatible wallets.

### What if I lose access to my wallet?

Your wallet is your identity in the system. If you lose access:
- You lose access to your role and permissions
- Contact the admin to assign your role to a new address
- **Always backup your wallet seed phrase securely**

### How much do transactions cost?

Transaction costs (gas fees) vary based on:
- Network congestion
- Selected blockchain (Polygon is cheaper than Ethereum)
- Complexity of the transaction

Typical costs:
- Create project: 0.01-0.05 ETH
- Upload document: 0.005-0.02 ETH
- Request/approve payment: 0.003-0.01 ETH

### Can I delete a document?

No. Documents stored on IPFS and recorded on the blockchain are permanent. This ensures data integrity and prevents tampering. Only upload documents you're certain about.

### How do I report a bug?

1. Open an issue on the GitHub repository
2. Include:
   - Description of the problem
   - Steps to reproduce
   - Screenshots (if applicable)
   - Your wallet address (optional)
   - Network and browser information

## Getting Help

Need more assistance?

- 📖 Check the [README.md](README.md) for technical details
- 🚀 Review the [DEPLOYMENT_GUIDE.md](DEPLOYMENT_GUIDE.md) for setup instructions
- 💬 Join our community channels
- 🐛 Report bugs on GitHub

## Tips for Success

1. **Test First**: Always test on a testnet before using real funds
2. **Save Addresses**: Keep a record of important addresses and transaction hashes
3. **Verify Recipients**: Double-check payment recipient addresses
4. **Monitor Gas**: Be aware of gas costs and adjust accordingly
5. **Backup Data**: Keep local backups of important document hashes
6. **Stay Updated**: Watch for application updates and improvements
7. **Secure Your Wallet**: Never share your private keys or seed phrase

## Conclusion

The EPC Project Manager provides a transparent, secure, and efficient way to manage construction projects using blockchain technology. Take time to familiarize yourself with the interface and always practice on testnets first.

Happy project managing! 🏗️✨
