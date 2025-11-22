# Project Structure - EPC Project Manager

Complete overview of the project architecture and file organization.

## 📁 Directory Structure

```
epc-project-manager/
├── public/                          # Static files
│   └── index.html                   # HTML template
│
├── src/                             # Source code
│   ├── components/                  # Reusable UI components
│   │   ├── Header.js               # Top navigation bar with wallet
│   │   └── Sidebar.js              # Side navigation menu
│   │
│   ├── contexts/                    # React Context providers
│   │   └── Web3Context.js          # Web3 connection & state management
│   │
│   ├── pages/                       # Main application pages
│   │   ├── Dashboard.js            # Overview & statistics
│   │   ├── Projects.js             # Project CRUD operations
│   │   ├── Documents.js            # IPFS document management
│   │   ├── Payments.js             # Payment request workflow
│   │   ├── Team.js                 # Role & permission management
│   │   └── Settings.js             # App configuration
│   │
│   ├── contracts/                   # Smart contract interfaces
│   │   └── config.js               # ABIs, addresses, networks
│   │
│   ├── App.js                       # Main app component & routing
│   ├── index.js                     # Application entry point
│   └── index.css                    # Global styles & Tailwind
│
├── .env.example                     # Environment template
├── .gitignore                       # Git ignore rules
├── package.json                     # Dependencies & scripts
├── package-lock.json               # Dependency lock file
├── tailwind.config.js              # Tailwind CSS configuration
├── postcss.config.js               # PostCSS configuration
│
├── README.md                        # Project documentation
├── QUICK_START.md                  # Quick setup guide
├── DEPLOYMENT_GUIDE.md             # Deployment instructions
├── USER_GUIDE.md                   # End-user manual
└── PROJECT_STRUCTURE.md            # This file
```

## 🏗️ Architecture Overview

### Frontend Architecture

```
┌─────────────────────────────────────────────────┐
│                   Browser                        │
│  ┌──────────────────────────────────────────┐  │
│  │          React Application                │  │
│  │                                            │  │
│  │  ┌────────────┐      ┌─────────────────┐ │  │
│  │  │   Pages    │◄────►│   Components    │ │  │
│  │  └────────────┘      └─────────────────┘ │  │
│  │         │                     │            │  │
│  │         ▼                     ▼            │  │
│  │  ┌─────────────────────────────────────┐ │  │
│  │  │        Web3Context                   │ │  │
│  │  │  - Wallet connection                 │ │  │
│  │  │  - Contract instances                │ │  │
│  │  │  - User role management              │ │  │
│  │  └─────────────────────────────────────┘ │  │
│  │                   │                        │  │
│  └───────────────────┼────────────────────────┘  │
│                      │                            │
└──────────────────────┼────────────────────────────┘
                       │
                       ▼
              ┌────────────────┐
              │   MetaMask     │
              │   (Web3)       │
              └────────────────┘
                       │
                       ▼
              ┌────────────────┐
              │   Blockchain   │
              │   - Ethereum   │
              │   - Polygon    │
              │   - etc.       │
              └────────────────┘
```

### Smart Contract Architecture

```
┌────────────────────────────────────────────┐
│         EPCProjectManager                   │
│  (Main orchestration contract)              │
│                                              │
│  - Creates projects                          │
│  - Manages team members                      │
│  - Coordinates sub-contracts                 │
└──────────────┬──────────────┬───────────────┘
               │              │
       ┌───────┴──────┐  ┌───┴─────────┐
       │              │  │             │
       ▼              ▼  ▼             ▼
┌──────────────┐ ┌─────────────┐ ┌─────────────┐
│ Document     │ │   Escrow    │ │  Payment    │
│ Manager      │ │   Manager   │ │  Approval   │
│              │ │             │ │  Manager    │
│ - Upload     │ │ - Deposit   │ │ - Request   │
│ - View       │ │ - Release   │ │ - Approve   │
│ - Access     │ │ - Track     │ │ - Execute   │
└──────────────┘ └─────────────┘ └─────────────┘
```

## 📄 Key Files Explained

### Core Application Files

#### `src/App.js`
- Main application component
- Sets up routing with React Router
- Wraps app in Web3Provider
- Manages sidebar state
- Configures toast notifications

#### `src/index.js`
- Application entry point
- Renders React app to DOM
- Imports global CSS

#### `src/index.css`
- Global styles
- Tailwind CSS imports
- Custom animations
- Scrollbar styling

### Context & State Management

#### `src/contexts/Web3Context.js`
**Purpose**: Centralized Web3 state management

**Provides**:
- `account`: Connected wallet address
- `provider`: ethers.js provider
- `signer`: ethers.js signer
- `contract`: Main contract instance
- `chainId`: Current network ID
- `userRole`: User's role in the system
- `connectWallet()`: Connect wallet function
- `disconnectWallet()`: Disconnect function
- `switchNetwork()`: Network switching

**Key Features**:
- Automatic wallet detection
- Account change handling
- Network change handling
- Contract initialization
- Role detection

### Components

#### `src/components/Header.js`
**Features**:
- Wallet connection button
- Display connected address
- Show current network
- Menu toggle for sidebar
- Disconnect wallet option

#### `src/components/Sidebar.js`
**Features**:
- Navigation menu
- Active route highlighting
- Icon-based navigation
- Collapsible design

### Pages

#### `src/pages/Dashboard.js`
**Purpose**: Overview and statistics

**Features**:
- Project count display
- Active projects metric
- Document statistics
- Payment queue info
- Recent activity feed
- Quick action buttons

#### `src/pages/Projects.js`
**Purpose**: Project management

**Features**:
- Create new projects (admin)
- List all projects
- View project details
- Fund projects
- Complete projects
- Project status indicators

**Contract Interactions**:
- `createProject()`
- `getProjectDetails()`
- `fundProject()`
- `completeProject()`

#### `src/pages/Documents.js`
**Purpose**: Document management

**Features**:
- Upload documents to IPFS
- View document list
- Document metadata display
- IPFS link generation
- Access control

**Contract Interactions**:
- `uploadDocument()`
- `getDocument()`

#### `src/pages/Payments.js`
**Purpose**: Payment workflow

**Features**:
- Request payments (contractor)
- Approve requests (consultant)
- Execute payments (project manager)
- Payment status tracking
- Approval progress display

**Contract Interactions**:
- `requestPayment()`
- `approve()`
- `execute()`

#### `src/pages/Team.js`
**Purpose**: Team and role management

**Features**:
- Role overview
- Permission descriptions
- Add consultants
- Role hierarchy display

**Contract Interactions**:
- `addConsultant()`

#### `src/pages/Settings.js`
**Purpose**: App configuration

**Features**:
- Wallet information
- Network switching
- Contract details
- Application info
- Documentation links

### Contract Configuration

#### `src/contracts/config.js`
**Contains**:
- Contract address from env
- Main contract ABI
- Document manager ABI
- Escrow manager ABI
- Payment manager ABI
- Network configurations

**Network Support**:
- Ethereum Mainnet (1)
- Goerli Testnet (5)
- Sepolia Testnet (11155111)
- Polygon Mainnet (137)
- Mumbai Testnet (80001)
- Localhost (31337)

## 🎨 Styling Architecture

### Tailwind CSS Configuration

**Theme Extensions** (`tailwind.config.js`):
- Primary color palette (indigo)
- Secondary color palette (purple)
- Custom gradients
- Responsive breakpoints

### Custom CSS

**Animations** (`src/index.css`):
- `fadeIn`: Smooth page transitions
- `pulse`: Loading indicators
- Custom scrollbar styling

### Design System

**Color Scheme**:
- Primary: Indigo (#667eea)
- Secondary: Purple (#a855f7)
- Success: Green
- Warning: Yellow
- Error: Red
- Info: Blue

**Components**:
- Cards: White background, rounded corners, shadow
- Buttons: Gradient backgrounds, hover effects
- Inputs: Border focus states, ring effect
- Badges: Role-based color coding

## 🔐 Security Features

### Smart Contract Level
- Role-based access control (OpenZeppelin)
- Reentrancy protection
- Multi-signature approval
- Escrow mechanism

### Frontend Level
- Wallet signature verification
- Role checking before UI actions
- Transaction confirmation prompts
- Input validation

## 🚀 Performance Considerations

### Optimization Techniques
- React.StrictMode for development
- Lazy loading (can be added)
- Memoization opportunities
- Efficient state management

### Best Practices
- Minimize re-renders
- Batch state updates
- Optimize contract calls
- Cache blockchain data

## 🧪 Testing Strategy

### Recommended Tests
1. **Unit Tests**: Individual component testing
2. **Integration Tests**: Page-level functionality
3. **Contract Tests**: Smart contract behavior
4. **E2E Tests**: Full user workflows

### Test Files (to be added)
```
src/
├── __tests__/
│   ├── components/
│   ├── pages/
│   └── contexts/
```

## 📦 Dependencies

### Core Dependencies
- **react**: UI framework
- **react-dom**: React rendering
- **react-router-dom**: Navigation
- **ethers**: Web3 library
- **react-toastify**: Notifications

### UI Dependencies
- **@heroicons/react**: Icon library
- **@headlessui/react**: Accessible components
- **tailwindcss**: Utility CSS framework

### Build Tools
- **react-scripts**: Build tooling
- **postcss**: CSS processing
- **autoprefixer**: CSS vendor prefixes

## 🔄 Data Flow

### Creating a Project
```
User Input → Form → createProject() → Smart Contract
                                          ↓
                                    Transaction
                                          ↓
                                    Event Emitted
                                          ↓
                                    UI Updates
```

### Payment Workflow
```
1. Request:  Contractor → requestPayment() → Contract
2. Approve:  Consultant → approve() → Contract (x2)
3. Execute:  PM → execute() → Contract → Escrow Release
```

## 🌐 Deployment Flow

```
Development → Build → Deploy → Configure → Test → Production
     ↓           ↓        ↓         ↓         ↓         ↓
  npm start   npm build  Vercel   .env    Manual   Monitor
                         Netlify  vars    tests    errors
                         IPFS
```

## 📝 Notes

- All pages are responsive (mobile-friendly)
- Dark mode can be added in future
- i18n support can be added for localization
- More contract interactions can be exposed
- Analytics can be integrated

## 🔮 Future Enhancements

Potential additions:
- [ ] User profiles and avatars
- [ ] Project milestones
- [ ] Budget tracking charts
- [ ] Email notifications
- [ ] File preview for documents
- [ ] Advanced search and filters
- [ ] Export data to CSV/PDF
- [ ] Multi-language support
- [ ] Dark mode theme
- [ ] Mobile app version

## 📚 Related Documentation

- **README.md**: Overview and features
- **QUICK_START.md**: Fast setup guide
- **DEPLOYMENT_GUIDE.md**: Production deployment
- **USER_GUIDE.md**: End-user instructions

---

This structure provides a solid foundation for a production-ready Web3 application. The modular design makes it easy to extend and maintain.
