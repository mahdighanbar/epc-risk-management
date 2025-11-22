# EPC Project Manager - Deployment Guide

This guide will walk you through deploying the smart contracts and setting up the React application.

## Table of Contents
1. [Smart Contract Deployment](#smart-contract-deployment)
2. [Frontend Setup](#frontend-setup)
3. [Environment Configuration](#environment-configuration)
4. [Testing](#testing)
5. [Production Deployment](#production-deployment)

## Smart Contract Deployment

### Prerequisites
- Remix IDE (https://remix.ethereum.org) or Hardhat/Truffle
- MetaMask wallet with test ETH
- Access to a testnet (Sepolia, Goerli, or Mumbai recommended)

### Using Remix IDE

1. **Open Remix IDE**: Navigate to https://remix.ethereum.org

2. **Create the Contract File**:
   - Create a new file named `EPCProjectManager.sol`
   - Copy and paste your smart contract code

3. **Compile the Contract**:
   - Go to the "Solidity Compiler" tab
   - Select compiler version `0.8.20`
   - Click "Compile EPCProjectManager.sol"

4. **Deploy the Contract**:
   - Go to the "Deploy & Run Transactions" tab
   - Select "Injected Provider - MetaMask" as the environment
   - Connect your MetaMask wallet
   - Ensure you're on the correct network (e.g., Sepolia)
   - Click "Deploy"
   - Confirm the transaction in MetaMask

5. **Save Contract Information**:
   - After deployment, copy the contract address
   - Save it for the frontend configuration

### Using Hardhat (Advanced)

If you prefer to use Hardhat:

```bash
# Create a new Hardhat project
npx hardhat init

# Install dependencies
npm install --save-dev @nomicfoundation/hardhat-toolbox

# Create deployment script
# Create a file: scripts/deploy.js
```

Example deployment script:
```javascript
const hre = require("hardhat");

async function main() {
  const EPCProjectManager = await hre.ethers.getContractFactory("EPCProjectManager");
  const epcManager = await EPCProjectManager.deploy();
  await epcManager.deployed();

  console.log("EPCProjectManager deployed to:", epcManager.address);
}

main().catch((error) => {
  console.error(error);
  process.exitCode = 1;
});
```

Deploy:
```bash
npx hardhat run scripts/deploy.js --network sepolia
```

## Frontend Setup

### 1. Install Dependencies

```bash
npm install
```

### 2. Configure Tailwind CSS

The project is already configured with Tailwind CSS. If you encounter issues:

```bash
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
```

### 3. Environment Configuration

Create a `.env` file in the root directory:

```bash
cp .env.example .env
```

Edit `.env` and add your contract address:

```
REACT_APP_CONTRACT_ADDRESS=0xYourContractAddressHere
```

### 4. Start Development Server

```bash
npm start
```

The app will be available at http://localhost:3000

## Environment Configuration

### Network Configuration

The application supports multiple networks. To add a custom network:

1. Open `src/contracts/config.js`
2. Add your network to the `NETWORKS` object:

```javascript
export const NETWORKS = {
  // ... existing networks
  12345: { name: 'Your Custom Network', currency: 'ETH' },
};
```

### Contract Address Management

For different environments, you can create multiple `.env` files:

- `.env.development` - Development environment
- `.env.production` - Production environment
- `.env.test` - Testing environment

Example:
```
# .env.development
REACT_APP_CONTRACT_ADDRESS=0xDevContractAddress

# .env.production
REACT_APP_CONTRACT_ADDRESS=0xProdContractAddress
```

## Testing

### Testing Smart Contracts

Before deploying, test your contracts thoroughly:

1. **Using Remix IDE**:
   - Deploy to JavaScript VM
   - Test all functions manually
   - Verify access control and permissions

2. **Using Hardhat**:
```bash
npx hardhat test
```

### Testing the Frontend

```bash
# Run tests
npm test

# Run tests with coverage
npm test -- --coverage
```

### Manual Testing Checklist

- [ ] Connect wallet successfully
- [ ] Create a new project (as admin)
- [ ] Fund a project
- [ ] Upload a document (as contractor)
- [ ] Request a payment (as contractor)
- [ ] Approve a payment (as consultant)
- [ ] Execute a payment (as project manager)
- [ ] Add a consultant to project
- [ ] Complete a project
- [ ] View all data correctly

## Production Deployment

### Building for Production

```bash
npm run build
```

This creates an optimized production build in the `build` folder.

### Deployment Options

#### Option 1: Vercel (Recommended)

1. Install Vercel CLI:
```bash
npm install -g vercel
```

2. Deploy:
```bash
vercel
```

3. Set environment variables in Vercel dashboard

#### Option 2: Netlify

1. Install Netlify CLI:
```bash
npm install -g netlify-cli
```

2. Deploy:
```bash
netlify deploy --prod
```

3. Set environment variables in Netlify dashboard

#### Option 3: IPFS (Decentralized)

1. Build the application:
```bash
npm run build
```

2. Upload to IPFS:
```bash
# Using Pinata
# Upload the build folder to https://pinata.cloud

# Using IPFS Desktop
# Add the build folder to IPFS Desktop
```

3. Access via IPFS gateway:
```
https://ipfs.io/ipfs/YOUR_IPFS_HASH
```

#### Option 4: Traditional Web Server

1. Build the application:
```bash
npm run build
```

2. Copy the `build` folder to your web server

3. Configure web server (example for Nginx):
```nginx
server {
    listen 80;
    server_name yourdomain.com;
    root /path/to/build;
    index index.html;

    location / {
        try_files $uri $uri/ /index.html;
    }
}
```

### Post-Deployment Checklist

- [ ] Verify contract address is correct
- [ ] Test wallet connection on production
- [ ] Test all major features
- [ ] Check console for errors
- [ ] Verify mobile responsiveness
- [ ] Test on different browsers
- [ ] Monitor gas costs
- [ ] Set up error tracking (e.g., Sentry)

## Security Best Practices

1. **Never commit `.env` files**: Always use `.env.example` as a template
2. **Use testnet first**: Thoroughly test on testnet before mainnet
3. **Audit smart contracts**: Consider professional audit for production
4. **Monitor transactions**: Set up monitoring for contract interactions
5. **Implement rate limiting**: Protect against spam and abuse
6. **Use HTTPS**: Always serve the app over HTTPS in production
7. **Verify contract source code**: Publish and verify on Etherscan

## Monitoring and Maintenance

### Contract Monitoring

Use tools like:
- **Etherscan**: Monitor transactions and events
- **The Graph**: Index and query blockchain data
- **Tenderly**: Real-time monitoring and alerting

### Application Monitoring

Consider implementing:
- **Sentry**: Error tracking and monitoring
- **Google Analytics**: User behavior analytics
- **LogRocket**: Session replay and debugging

## Troubleshooting

### Common Issues

1. **MetaMask not connecting**:
   - Clear browser cache
   - Reset MetaMask account
   - Check network configuration

2. **Transaction failures**:
   - Insufficient gas
   - Incorrect permissions/roles
   - Contract address mismatch

3. **Build errors**:
   - Clear node_modules and reinstall
   - Check Node.js version (v16+ required)
   - Verify all dependencies are installed

### Getting Help

- Check the README.md for basic information
- Open an issue on GitHub
- Join the community Discord/Telegram
- Contact the development team

## Upgrading

When updating the smart contracts:

1. Deploy new contract version
2. Update `REACT_APP_CONTRACT_ADDRESS` in `.env`
3. Update contract ABIs in `src/contracts/config.js`
4. Test thoroughly on testnet
5. Rebuild and redeploy frontend
6. Migrate data if necessary
7. Communicate changes to users

## License

This deployment guide is part of the EPC Project Manager application licensed under MIT License.
