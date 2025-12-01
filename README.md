# HackX

**Trustless. Transparent. Unstoppable hackathons on IPFS and Smart Contracts.**

HackX is a decentralized hackathon platform that leverages blockchain technology and IPFS for transparent, trustless hackathon management. Organizers can create hackathons, participants can submit projects, and judges can evaluate submissions—all powered by smart contracts.

---

## ✨ Features

- 🏗️ **Smart Contract Based**: Fully decentralized hackathon management
- 📁 **IPFS Storage**: Decentralized storage for hackathon and project data
- 🎯 **Multi-role Support**: Organizers, participants, and judges
- 🗳️ **Transparent Judging**: On-chain scoring and feedback system
- 👥 **Team Management**: Collaborative project development
- 🕒 **Time-gated Phases**: Registration → Submission → Judging
- 🔐 **Wallet Integration**: Browser Wallet and Web3 authentication

---

## 🚀 Quick Start

### Prerequisites

- [Bun](https://bun.sh) (v1.0+) or Node.js (v20+)
- Browser wallet extension (MetaMask, Rabby Wallet, etc.)
- Git

### Installation

```bash
# Clone the repository
git clone <your-repository-url>
cd HackX-minor

# Install dependencies
bun install

# Copy environment file
cp .env.example .env

# Start development server
bun dev
```

Visit `http://localhost:3000` to see the application.

### Environment Setup

Update your `.env` file with the following:

```env
NEXT_PUBLIC_THIRDWEB_CLIENT_ID=your_thirdweb_client_id
NEXT_PUBLIC_CONTRACT_ADDRESS=your_smart_contract_address
NEXT_PUBLIC_BASE_URL=http://localhost:3000/
NEXT_PUBLIC_EXPLORER_URL=https://sepolia.basescan.org/
```

**Get API Keys:**
- **Thirdweb Client ID**: Visit [thirdweb.com/dashboard](https://thirdweb.com/dashboard) → Create project → Copy Client ID

### Deploy Smart Contract

1. Open [Remix IDE](https://remix.ethereum.org/)
2. Create `HackX.sol` and copy contents from `contract.sol`
3. Compile with Solidity 0.8.28+
4. Deploy to Base Sepolia testnet
5. Copy the contract address to your `.env` file

> 📖 For detailed deployment instructions, see [SETUP.md](./SETUP.md)

---

## 📖 How to Use the Platform

### 🎯 For Organizers

Organizers can create and manage hackathons on the platform.

#### Step 1: Connect Your Wallet
1. Click **"Connect Wallet"** in the top-right corner
2. Select your preferred wallet (MetaMask, Rabby, etc.)
3. Approve the connection request
4. Ensure you're on the **Base Sepolia** network

#### Step 2: Create a Hackathon
1. Navigate to **"Hackathons"** from the sidebar
2. Click **"Create Hackathon"** button
3. Fill in the hackathon details:
   - **Name**: Your hackathon title
   - **Description**: Detailed information about the event
   - **Prize Pool**: Total prize amount (in ETH)
   - **Registration Period**: Start and end dates for registration
   - **Submission Period**: When participants can submit projects
   - **Judging Period**: When judges can evaluate submissions
   - **Banner Image**: Upload a cover image for your hackathon
4. Click **"Create Hackathon"** and confirm the transaction
5. Wait for the transaction to be confirmed on-chain

#### Step 3: Add Judges
1. Go to your hackathon's detail page
2. Click **"Add Judge"** button
3. Enter the judge's wallet address
4. Confirm the transaction
5. The judge will need to accept the invitation

#### Step 4: Monitor Your Hackathon
1. View registered participants in the **"Participants"** tab
2. Track project submissions during the submission period
3. Monitor judging progress during the judging phase
4. View final results and rankings after judging ends

---

### 👨‍💻 For Participants

Participants can register for hackathons and submit their projects.

#### Step 1: Connect Your Wallet
1. Click **"Connect Wallet"** in the top-right corner
2. Approve the connection with your wallet
3. Switch to **Base Sepolia** network if prompted

#### Step 2: Browse Hackathons
1. Navigate to **"Hackathons"** from the sidebar
2. Browse available hackathons
3. Filter by status: **Active**, **Upcoming**, or **Past**
4. Click on a hackathon to view details

#### Step 3: Register for a Hackathon
1. Open the hackathon detail page
2. Review the requirements and timeline
3. Click **"Register"** button
4. Confirm the transaction in your wallet
5. Wait for confirmation

#### Step 4: Create a Project
1. Navigate to **"Projects"** from the sidebar
2. Click **"Create Project"** button
3. Fill in project details:
   - **Project Name**: Your project title
   - **Description**: What your project does
   - **Technology Stack**: Technologies used
   - **GitHub Repository**: Link to your code
   - **Demo URL**: Live demo link (optional)
   - **Team Members**: Add team member wallet addresses
4. Click **"Create Project"** and confirm the transaction

#### Step 5: Submit Your Project
1. Go to your project page
2. Ensure all information is complete and accurate
3. Click **"Submit to Hackathon"** button
4. Select the hackathon you want to submit to
5. Confirm the submission transaction
6. You can only submit during the **submission period**

#### Step 6: Track Your Submission
1. View your project status on the project page
2. Check for judge feedback during the judging period
3. View your scores and rankings after judging ends

---

### ⚖️ For Judges

Judges evaluate project submissions and provide scores.

#### Step 1: Connect Your Wallet
1. Click **"Connect Wallet"** in the top-right corner
2. Connect with the wallet address the organizer added
3. Ensure you're on **Base Sepolia** network

#### Step 2: Accept Judge Invitation
1. Navigate to **"Judge"** from the sidebar
2. View your pending judge invitations
3. Click **"Accept"** on the hackathon invitation
4. Confirm the transaction

#### Step 3: View Submissions
1. Go to the hackathon's judge panel
2. View all submitted projects
3. Click on a project to see full details:
   - Project description
   - Demo and repository links
   - Team information
   - Technology stack

#### Step 4: Evaluate Projects
1. Open a project submission
2. Review the project thoroughly
3. Provide scores based on criteria:
   - **Innovation**: Creativity and uniqueness (0-100)
   - **Technical Complexity**: Implementation quality (0-100)
   - **Design**: UI/UX and presentation (0-100)
   - **Impact**: Potential real-world impact (0-100)
4. Write detailed feedback for the team
5. Click **"Submit Evaluation"** and confirm the transaction

#### Step 5: Complete Judging
1. Evaluate all assigned projects before the judging period ends
2. Review your submitted scores
3. Final rankings are calculated automatically based on all judges' scores

---

## 🛠️ Tech Stack

- **Frontend**: Next.js 15, React 19, TypeScript
- **Styling**: Tailwind CSS, Framer Motion
- **Web3**: thirdweb SDK, Wallet integration
- **Smart Contracts**: Solidity, OpenZeppelin
- **Blockchain**: Base Sepolia Network
- **Storage**: IPFS (via Pinata/ThirdWeb SDK)
- **UI Components**: ShadCN UI, Radix UI, Lucide Icons
- **Package Manager**: Bun
- **Code Quality**: Biome (linting & formatting)

---

## 🏗️ Project Structure

```
HackX/
├── src/
│   ├── app/                    # Next.js app router
│   │   ├── dashboard/          # Dashboard page
│   │   ├── hackathons/         # Hackathon pages
│   │   ├── projects/           # Project pages
│   │   └── judge/              # Judge panel pages
│   ├── components/             # React components
│   │   ├── layout/             # Layout components
│   │   ├── ui/                 # UI components (ShadCN)
│   │   └── ...                 # Feature components
│   ├── constants/              # Configuration constants
│   ├── data/                   # Mock data and utilities
│   └── hooks/                  # Custom React hooks
├── public/                     # Static assets
├── contract.sol                # HackX smart contract
├── SETUP.md                    # Detailed setup guide
├── .env.example                # Environment variables template
└── package.json                # Dependencies
```

---

## 🔧 Available Scripts

```bash
# Development
bun dev              # Start development server at localhost:3000

# Production
bun run build        # Build for production
bun start            # Start production server

# Code Quality
bun run lint         # Run Biome linter
bun run format       # Format code with Biome
```

---

## 🌐 Network Information

**Base Sepolia Testnet**
- Chain ID: 84532
- RPC URL: https://sepolia.base.org
- Block Explorer: https://sepolia.basescan.org
- Faucet: Get test ETH from [Base Sepolia Faucet](https://www.alchemy.com/faucets/base-sepolia)

---

## 🔐 Security Best Practices

1. **Never commit your `.env` file** - It contains sensitive API keys
2. **Use testnet for development** - Don't deploy to mainnet until thoroughly tested
3. **Verify smart contracts** - Always verify contracts on block explorers
4. **Test wallet integration** - Ensure proper wallet connection handling
5. **Validate user inputs** - All form inputs are validated before blockchain transactions

---

## 🐛 Troubleshooting

### Wallet Connection Issues
- Ensure you're on the Base Sepolia network
- Clear browser cache and reconnect wallet
- Try a different wallet provider

### Transaction Failures
- Check you have enough test ETH for gas fees
- Verify you're within the correct time period (registration/submission/judging)
- Ensure you haven't already performed the action (e.g., already registered)

### IPFS Upload Issues
- Check your Thirdweb Client ID is correct
- Verify your internet connection
- Try uploading smaller files

---

## 📄 License

MIT License - see [LICENSE](./LICENSE) file for details.

---

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

---

**Built with ❤️ for the Web3 community**
