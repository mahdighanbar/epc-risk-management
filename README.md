# EPC Project Manager - React DApp

A decentralized application (DApp) for managing EPC (Engineering, Procurement, and Construction) projects using blockchain technology.

## Features

- 🏗️ **Project Management**: Create and manage construction projects on the blockchain
- 📄 **Document Storage**: Upload and manage project documents using IPFS
- 💰 **Payment System**: Request, approve, and execute payments with multi-signature approval
- 👥 **Team Management**: Assign roles and permissions (Admin, Project Manager, Contractor, Consultant)
- 🔐 **Access Control**: Role-based permissions using OpenZeppelin's AccessControl
- 💸 **Escrow**: Secure fund management with built-in escrow functionality

## Smart Contract Overview

The application interacts with four main smart contracts:

1. **EPCProjectManager**: Main contract orchestrating all functionality
2. **DataConfidentialityManager**: Handles document uploads and access control
3. **EscrowManager**: Manages project funds in escrow
4. **PaymentApprovalManager**: Multi-signature payment approval workflow

## Prerequisites

- Node.js (v16 or higher)
- MetaMask or another Web3 wallet
- Access to an Ethereum-compatible network

## Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd epc-project-manager
```

2. Install dependencies:
```bash
npm install
```

3. Create a `.env` file in the root directory:
```bash
cp .env.example .env
```

4. Configure your environment variables in `.env`:
```
REACT_APP_CONTRACT_ADDRESS=your_deployed_contract_address
```

## Running the Application

Start the development server:
```bash
npm start
```

The application will open at [http://localhost:3000](http://localhost:3000)

## Building for Production

Create a production build:
```bash
npm run build
```

## Smart Contract Deployment

Before using the application, you need to deploy the smart contracts:

1. Deploy the `EPCProjectManager` contract to your chosen network
2. Copy the deployed contract address
3. Add it to your `.env` file as `REACT_APP_CONTRACT_ADDRESS`

## Application Structure

```
src/
├── components/          # Reusable UI components
│   ├── Header.js       # Top navigation bar
│   └── Sidebar.js      # Side navigation menu
├── contexts/           # React Context providers
│   └── Web3Context.js  # Web3 and wallet connection logic
├── pages/              # Main application pages
│   ├── Dashboard.js    # Overview and statistics
│   ├── Projects.js     # Project management
│   ├── Documents.js    # Document management
│   ├── Payments.js     # Payment requests and approvals
│   ├── Team.js         # Role and permission management
│   └── Settings.js     # Application settings
├── contracts/          # Contract ABIs and configuration
│   └── config.js       # Contract addresses and ABIs
├── App.js              # Main application component
└── index.js            # Application entry point
```

## User Roles

### Admin (👑)
- Create and manage projects
- Assign project managers and contractors
- Add consultants to projects
- Full system control

### Project Manager (📋)
- Execute approved payment requests
- Complete projects
- Add consultants to their projects
- View project documents

### Contractor (🔨)
- Upload project documents
- Request payments
- View project details

### Consultant (✅)
- Approve payment requests
- View project documents
- Review project progress

### Viewer (👁️)
- View project documents
- Read-only access

## Key Features

### Dashboard
- Overview of total and active projects
- Document and payment statistics
- Recent activity feed
- Quick action buttons

### Projects
- Create new projects with budget and team assignment
- Fund projects with cryptocurrency
- View project details and balances
- Complete projects when finished

### Documents
- Upload documents to IPFS
- View and manage project documents
- Access control based on user roles
- Permanent, decentralized storage

### Payments
- Request payments as a contractor
- Approve payment requests as a consultant
- Execute approved payments as project manager
- Multi-signature approval workflow

### Team Management
- Add consultants to projects
- View role hierarchy and permissions
- Understand available roles

### Settings
- View wallet and contract information
- Switch between networks
- Access documentation and resources

## Technologies Used

- **React 18**: Frontend framework
- **ethers.js 6**: Web3 library for Ethereum interaction
- **React Router**: Navigation and routing
- **Tailwind CSS**: Utility-first CSS framework
- **Heroicons**: Beautiful hand-crafted SVG icons
- **React Toastify**: Toast notifications
- **Headless UI**: Unstyled, accessible UI components

## Network Support

The application supports multiple Ethereum-compatible networks:
- Ethereum Mainnet
- Goerli Testnet
- Sepolia Testnet
- Polygon Mainnet
- Mumbai Testnet
- Localhost (for development)

## Security Considerations

- All smart contract interactions require wallet signatures
- Role-based access control enforced at contract level
- Multi-signature approval for payments
- Escrow system protects project funds
- IPFS for tamper-proof document storage

## Development

### Adding New Features

1. Create new components in `src/components/`
2. Add new pages in `src/pages/`
3. Update routes in `src/App.js`
4. Update contract ABIs in `src/contracts/config.js` if needed

### Styling

The application uses Tailwind CSS. Customize the theme in `tailwind.config.js`.

## Troubleshooting

### MetaMask Connection Issues
- Ensure MetaMask is installed and unlocked
- Check that you're on the correct network
- Try refreshing the page

### Contract Interaction Errors
- Verify the contract address in `.env`
- Ensure you have the correct role for the action
- Check that you have sufficient gas

### IPFS Upload Issues
- Upload files to IPFS separately using services like:
  - Pinata (https://pinata.cloud)
  - Infura IPFS (https://infura.io/product/ipfs)
  - Web3.Storage (https://web3.storage)
- Copy the IPFS hash and paste it in the document upload form

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License.

## Support

For issues and questions, please open an issue on the GitHub repository.

## Acknowledgments

- OpenZeppelin for secure smart contract libraries
- The Ethereum and IPFS communities
- All contributors to this project
