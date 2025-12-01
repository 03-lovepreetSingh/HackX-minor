# HackX Setup Guide

Complete guide to set up and deploy the HackX decentralized hackathon platform.

---

## 📋 Prerequisites

Before you begin, ensure you have the following installed:

- **Bun** (v1.0+) or **Node.js** (v20+)
  - Install Bun: `curl -fsSL https://bun.sh/install | bash`
  - Or install Node.js from [nodejs.org](https://nodejs.org/)
- **Git** - [Download Git](https://git-scm.com/downloads)
- **Browser Wallet Extension**
  - [MetaMask](https://metamask.io/)
  - [Rabby Wallet](https://rabby.io/)
  - Or any Web3-compatible wallet

---

## 🚀 Quick Start

### Step 1: Clone the Repository

```bash
git clone <your-repository-url>
cd HackX-minor
```

### Step 2: Install Dependencies

```bash
# Using Bun (recommended)
bun install

# Or using npm
npm install

# Or using yarn
yarn install
```

### Step 3: Set Up Environment Variables

```bash
# Copy the example environment file
cp .env.example .env
```

Edit the `.env` file with your configuration (see [Environment Configuration](#environment-configuration) below).

### Step 4: Run the Development Server

```bash
# Using Bun
bun dev

# Or using npm
npm run dev
```

Visit [http://localhost:3000](http://localhost:3000) to see your application running.

---

## 🔧 Environment Configuration

### Required Environment Variables

Open your `.env` file and configure the following variables:

```env
# Thirdweb Client ID (for IPFS and Web3 features)
NEXT_PUBLIC_THIRDWEB_CLIENT_ID=your_thirdweb_client_id

# Smart Contract Address (deployed HackX contract)
NEXT_PUBLIC_CONTRACT_ADDRESS=your_smart_contract_address

# Base URL (your application URL)
NEXT_PUBLIC_BASE_URL=http://localhost:3000/

# Block Explorer URL (for transaction verification)
NEXT_PUBLIC_EXPLORER_URL=https://sepolia.basescan.org/
```

### How to Get API Keys

#### 1. Thirdweb Client ID

1. Visit [thirdweb.com](https://thirdweb.com/)
2. Click **"Sign In"** and connect your wallet
3. Go to [Dashboard](https://thirdweb.com/dashboard)
4. Click **"Settings"** → **"API Keys"**
5. Click **"Create API Key"**
6. Name your key (e.g., "HackX Development")
7. Copy the **Client ID** and paste it into your `.env` file

---

## 📜 Smart Contract Deployment

You need to deploy the HackX smart contract to the Base Sepolia testnet.

### Method 1: Using Remix IDE (Recommended for Beginners)

#### Step 1: Set Up Your Wallet

1. Install MetaMask browser extension
2. Create or import a wallet
3. Add **Base Sepolia** network to MetaMask:
   - Network Name: `Base Sepolia`
   - RPC URL: `https://sepolia.base.org`
   - Chain ID: `84532`
   - Currency Symbol: `ETH`
   - Block Explorer: `https://sepolia.basescan.org`

#### Step 2: Get Test ETH

You need test ETH to deploy the contract and pay for gas fees.

1. Visit [Alchemy Base Sepolia Faucet](https://www.alchemy.com/faucets/base-sepolia)
2. Or [Base Sepolia Faucet](https://www.coinbase.com/faucets/base-ethereum-sepolia-faucet)
3. Enter your wallet address
4. Request test ETH (you'll receive ~0.1 ETH)

#### Step 3: Open Remix IDE

1. Go to [remix.ethereum.org](https://remix.ethereum.org/)
2. You'll see the Remix interface with a file explorer on the left

#### Step 4: Create Contract File

1. In the **File Explorer**, click the **"+"** icon (Create New File)
2. Name it `HackX.sol`
3. Open the `contract.sol` file from your project directory
4. Copy the **entire contents**
5. Paste it into `HackX.sol` in Remix
6. Remix will automatically import OpenZeppelin dependencies

#### Step 5: Compile the Contract

1. Click the **"Solidity Compiler"** icon in the left sidebar (looks like "S")
2. Select compiler version **0.8.28** or higher
3. Click **"Compile HackX.sol"** button
4. Wait for compilation to complete
5. Ensure you see a **green checkmark** ✓ (no errors)

#### Step 6: Deploy the Contract

1. Click the **"Deploy & Run Transactions"** icon (below the compiler icon)
2. In the **Environment** dropdown, select **"Injected Provider - MetaMask"**
3. MetaMask will pop up - click **"Connect"** to approve
4. Verify you're on **Base Sepolia** network (Chain ID: 84532)
5. In the **Contract** dropdown, select **"HackX"**
6. Click the **"Deploy"** button (orange)
7. MetaMask will pop up with transaction details
8. Review the gas fees and click **"Confirm"**
9. Wait for the transaction to be confirmed (10-30 seconds)

#### Step 7: Save Contract Address

1. After deployment, you'll see the contract under **"Deployed Contracts"**
2. Click the **copy icon** next to the contract address
3. **Save this address!** You'll need it for your `.env` file
4. Paste it into your `.env` as `NEXT_PUBLIC_CONTRACT_ADDRESS`

#### Step 8: Verify Contract (Optional but Recommended)

1. Go to [Base Sepolia Explorer](https://sepolia.basescan.org/)
2. Paste your contract address in the search bar
3. Click on the **"Contract"** tab
4. Click **"Verify and Publish"**
5. Follow the verification wizard:
   - Compiler Type: Solidity (Single file)
   - Compiler Version: 0.8.28
   - License: MIT
   - Paste your contract code
6. Submit for verification

---

### Method 2: Using Hardhat/Foundry (Advanced)

If you prefer using development frameworks:

#### Using Hardhat

```bash
# Install Hardhat
npm install --save-dev hardhat @nomicfoundation/hardhat-toolbox

# Initialize Hardhat project
npx hardhat init

# Copy contract.sol to contracts/HackX.sol
# Configure hardhat.config.js with Base Sepolia network

# Deploy
npx hardhat run scripts/deploy.js --network baseSepolia
```

#### Using Foundry

```bash
# Install Foundry
curl -L https://foundry.paradigm.xyz | bash
foundryup

# Initialize Foundry project
forge init

# Copy contract.sol to src/HackX.sol

# Deploy
forge create --rpc-url https://sepolia.base.org \
  --private-key YOUR_PRIVATE_KEY \
  src/HackX.sol:HackX
```

---

## 🌐 Network Configuration

### Base Sepolia Testnet

This project uses the **Base Sepolia** testnet for development and testing.

**Network Details:**
- **Network Name**: Base Sepolia
- **RPC URL**: `https://sepolia.base.org`
- **Chain ID**: `84532`
- **Currency Symbol**: `ETH`
- **Block Explorer**: `https://sepolia.basescan.org`

### Adding Network to MetaMask

1. Open MetaMask
2. Click the network dropdown (top center)
3. Click **"Add Network"** → **"Add a network manually"**
4. Enter the network details above
5. Click **"Save"**

---

## 🏃‍♂️ Running the Application

### Development Mode

```bash
# Using Bun (fastest)
bun dev

# Using npm
npm run dev

# Using yarn
yarn dev
```

The application will be available at [http://localhost:3000](http://localhost:3000)

### Production Build

```bash
# Build the application
bun run build

# Start production server
bun start
```

### Code Quality

```bash
# Run linter
bun run lint

# Format code
bun run format
```

---

## 🧪 Testing the Setup

### 1. Test Wallet Connection

1. Open [http://localhost:3000](http://localhost:3000)
2. Click **"Connect Wallet"** in the top-right
3. Select your wallet and approve the connection
4. Verify your wallet address appears

### 2. Test Contract Interaction

1. Navigate to **"Hackathons"** page
2. Try creating a test hackathon
3. Fill in the form and submit
4. Approve the transaction in your wallet
5. Wait for confirmation
6. Verify the hackathon appears in the list

### 3. Test IPFS Upload

1. When creating a hackathon, upload a banner image
2. Verify the upload completes successfully
3. Check that the image displays correctly

---

## 🐛 Troubleshooting

### Common Issues and Solutions

#### Issue: "Cannot connect to wallet"
**Solution:**
- Ensure MetaMask is installed and unlocked
- Check you're on the Base Sepolia network
- Clear browser cache and try again
- Try a different browser

#### Issue: "Transaction failed"
**Solution:**
- Ensure you have enough test ETH for gas fees
- Check you're on the correct network (Base Sepolia)
- Increase gas limit in MetaMask settings
- Wait a few minutes and try again

#### Issue: "Contract not found"
**Solution:**
- Verify `NEXT_PUBLIC_CONTRACT_ADDRESS` in `.env` is correct
- Ensure the contract is deployed to Base Sepolia
- Check the contract address on [Base Sepolia Explorer](https://sepolia.basescan.org/)

#### Issue: "IPFS upload failed"
**Solution:**
- Verify `NEXT_PUBLIC_THIRDWEB_CLIENT_ID` is correct
- Check your internet connection
- Try uploading a smaller file
- Ensure the file is a valid image format

#### Issue: "Module not found" errors
**Solution:**
```bash
# Clear node_modules and reinstall
rm -rf node_modules
rm bun.lock  # or package-lock.json
bun install
```

#### Issue: "Port 3000 already in use"
**Solution:**
```bash
# Kill the process using port 3000
lsof -ti:3000 | xargs kill -9

# Or use a different port
PORT=3001 bun dev
```

---

## 📦 Deployment to Production

### Deploy to Vercel (Recommended)

1. Push your code to GitHub
2. Visit [vercel.com](https://vercel.com/)
3. Click **"Import Project"**
4. Select your GitHub repository
5. Configure environment variables:
   - Add all variables from your `.env` file
   - Update `NEXT_PUBLIC_BASE_URL` to your production URL
6. Click **"Deploy"**
7. Wait for deployment to complete

### Deploy to Other Platforms

The application can be deployed to any platform that supports Next.js:
- **Netlify**: [netlify.com](https://www.netlify.com/)
- **Railway**: [railway.app](https://railway.app/)
- **Render**: [render.com](https://render.com/)
- **AWS Amplify**: [aws.amazon.com/amplify](https://aws.amazon.com/amplify/)

---

## 🔐 Security Checklist

Before deploying to production:

- [ ] Never commit `.env` file to version control
- [ ] Use environment variables for all sensitive data
- [ ] Verify smart contract on block explorer
- [ ] Test all features on testnet before mainnet
- [ ] Enable rate limiting for API routes
- [ ] Implement proper error handling
- [ ] Use HTTPS in production
- [ ] Audit smart contract code
- [ ] Set up monitoring and logging

---

## 📚 Additional Resources

- [Next.js Documentation](https://nextjs.org/docs)
- [Thirdweb Documentation](https://portal.thirdweb.com/)
- [Base Network Documentation](https://docs.base.org/)
- [Solidity Documentation](https://docs.soliditylang.org/)
- [OpenZeppelin Contracts](https://docs.openzeppelin.com/contracts/)
- [IPFS Documentation](https://docs.ipfs.tech/)

---

## 🆘 Getting Help

If you encounter issues not covered in this guide:

1. Check the [GitHub Issues](your-repo-url/issues)
2. Review the [README.md](./README.md) for usage instructions
3. Consult the documentation links above
4. Create a new issue with detailed information about your problem

---

## ✅ Setup Verification Checklist

Use this checklist to ensure everything is set up correctly:

- [ ] Bun/Node.js installed
- [ ] Repository cloned
- [ ] Dependencies installed (`bun install`)
- [ ] `.env` file created and configured
- [ ] Thirdweb Client ID obtained and added
- [ ] MetaMask installed and configured
- [ ] Base Sepolia network added to wallet
- [ ] Test ETH obtained from faucet
- [ ] Smart contract deployed to Base Sepolia
- [ ] Contract address added to `.env`
- [ ] Development server running (`bun dev`)
- [ ] Wallet connection working
- [ ] Test transaction successful

---

**You're all set! 🎉**

Your HackX platform is now ready for development. Start by creating your first hackathon!
