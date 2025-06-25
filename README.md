# EduNFT - Blockchain Academic Certificates

EduNFT is a decentralized application built on the Aptos blockchain using the Move programming language. It enables educational institutions to issue verifiable academic certificates as soulbound NFTs, which students can share and third parties can verify.

## Features

- **Issuer Dashboard**: Educational institutions can mint soulbound NFTs as certificates
- **Student Dashboard**: Students can view their certificates and share them via QR codes
- **Verifier Page**: Third parties can verify the authenticity of certificates
- **Soulbound NFTs**: Non-transferable NFT certificates to ensure legitimacy

## Tech Stack

### Frontend
- React.js with Next.js
- Tailwind CSS for styling
- Aptos Wallet integration (Petra)
- QR code generation for certificate sharing

### Smart Contract
- Move language on Aptos blockchain
- Soulbound NFT implementation
- Certificate metadata storage

## Dependencies

### Frontend Dependencies
```bash
# Core dependencies
npm install next react react-dom
npm install aptos
npm install qrcode.react

# Development dependencies
npm install --save-dev autoprefixer postcss tailwindcss
npm install --save-dev eslint eslint-config-next
npm install --save-dev typescript @types/react @types/react-dom @types/node
```

### Blockchain Tools
```bash
# Install Aptos CLI
curl -fsSL "https://aptos.dev/scripts/install_cli.py" | python3

# Verify installation
aptos --version
```

## Getting Started

### Prerequisites

- Node.js (v16 or later)
- NPM or Yarn
- Aptos CLI (for contract deployment)
- Petra Wallet browser extension

### Installation

1. Clone the repository
```bash
git clone https://github.com/rajdeepdas108/EduNFT.git
cd EduNFT
```

2. Install frontend dependencies
```bash
cd client
npm install
# or
yarn install
```

3. Start the development server
```bash
npm run dev
# or
yarn dev
```

4. Open [http://localhost:3000](http://localhost:3000) with your browser

## Complete Deployment Guide

### 1. Smart Contract Deployment

1. Install Aptos CLI following the command above or the [official documentation](https://aptos.dev/cli-tools/aptos-cli-tool/install-aptos-cli/)

2. Create your deployment account and fund it (on Testnet)
```bash
# Initialize with a new profile
aptos init --profile eduNFT --network testnet

# Fund your account with test tokens from the faucet
aptos account fund-with-faucet --account <YOUR_ACCOUNT_ADDRESS> --amount 100000000 --network testnet
```

3. Compile and deploy the Move contract
```bash
cd contracts
aptos move compile --named-addresses eduNFT=<YOUR_ACCOUNT_ADDRESS>
aptos move publish --named-addresses eduNFT=<YOUR_ACCOUNT_ADDRESS> --network testnet
```

4. Verify the deployment
```bash
aptos account list --query resources --account <YOUR_ACCOUNT_ADDRESS> --network testnet
```

### 2. Frontend Configuration

1. Create environment variables file
```bash
cd client
touch .env.local
```

2. Add the following environment variables to `.env.local`
```
NEXT_PUBLIC_CONTRACT_ADDRESS=<YOUR_ACCOUNT_ADDRESS>
NEXT_PUBLIC_NETWORK=testnet
```

3. Build the frontend for production
```bash
npm run build
# or
yarn build
```

### 3. Frontend Deployment Options

#### Option 1: Deploy to Vercel (Recommended)

1. Install Vercel CLI
```bash
npm install -g vercel
```

2. Deploy to Vercel
```bash
vercel
```

3. For production deployment
```bash
vercel --prod
```

#### Option 2: Deploy to Netlify

1. Install Netlify CLI
```bash
npm install -g netlify-cli
```

2. Deploy to Netlify
```bash
netlify deploy
```

3. For production deployment
```bash
netlify deploy --prod
```

#### Option 3: Self-hosting

1. Build the application
```bash
npm run build
```

2. Start the production server
```bash
npm start
```

### 4. Production Deployment to Aptos Mainnet

When ready to deploy to Mainnet:

1. Initialize a new profile for Mainnet
```bash
aptos init --profile eduNFT_mainnet --network mainnet
```

2. Fund your account with actual APT tokens

3. Deploy the contract to Mainnet
```bash
cd contracts
aptos move publish --named-addresses eduNFT=<YOUR_MAINNET_ACCOUNT_ADDRESS> --network mainnet
```

4. Update your frontend environment variables for Mainnet
```
NEXT_PUBLIC_CONTRACT_ADDRESS=<YOUR_MAINNET_ACCOUNT_ADDRESS>
NEXT_PUBLIC_NETWORK=mainnet
```

5. Rebuild and redeploy your frontend

## Testing

### Smart Contract Testing
```bash
cd contracts
aptos move test
```

### Frontend Testing
```bash
cd client
npm run test
# or
yarn test
```

### End-to-End Testing with Cypress
```bash
npm install --save-dev cypress
npx cypress open
```

## CI/CD Pipeline Setup (GitHub Actions)

1. Create `.github/workflows/ci.yml` for continuous integration
2. Create `.github/workflows/deploy.yml` for continuous deployment

Example workflows available in the repository.

## Troubleshooting

### Common Issues

1. Wallet Connection Problems
   - Ensure Petra wallet is installed and on the correct network
   - Check browser console for connection errors

2. Contract Deployment Failures
   - Verify your account has sufficient funds
   - Check for syntax errors in the Move contract

3. Transaction Errors
   - Validate that function arguments match contract parameter types
   - Ensure gas fees are sufficient

For more help, join our Discord community or open an issue on GitHub.

## Usage

### For Institutions (Issuers)

1. Connect your Petra Wallet
2. Initialize yourself as an issuer
3. Fill out the certificate details:
   - Student wallet address
   - Certificate ID
   - Course name
   - Optional metadata URI
4. Submit to mint a certificate NFT

### For Students

1. Connect your Petra Wallet
2. View your certificates on the Student dashboard
3. Generate QR codes or shareable links for verification

### For Verifiers

1. Enter the student's wallet address or scan the QR code
2. View all verified certificates belonging to that address

## License

MIT

## Acknowledgements

- Aptos Blockchain
- Move Language
- Petra Wallet

Last Updated: 2025-06-25
