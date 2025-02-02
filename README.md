# Foundry Fund Me

A smart contract for crowdfunding built with Foundry. This project demonstrates a decentralized funding mechanism where users can fund the contract and only the owner can withdraw the funds.

## Getting Started

- [Foundry](https://book.getfoundry.sh/getting-started/installation)

### Installation

1. Clone the repository

```bash
git clone https://github.com/emhaihsan/foundry-fund-me
cd foundry-fund-me
```

2. Install dependencies

```bash
forge install
```

3. Build the project

```bash
forge build
```

### Configuration

1. Create a `.env` file in the root directory
2. Copy contents from `.env.example` and fill in your values:

```
SEPOLIA_RPC_URL=your_sepolia_rpc_url
MAINNET_RPC_URL=your_mainnet_rpc_url
ETHERSCAN_API_KEY=your_etherscan_api_key
PRIVATE_KEY=your_private_key
```

## Usage

### Testing

```bash
# Run all tests
forge test

# Run specific test
forge test --match-test testFunctionName

# Run tests with verbosity
forge test -vv

# Run tests with gas report
forge test --gas-report
```

### Deployment

1. To local network (Anvil):

```bash
# Start local network
anvil

# Deploy
forge script script/DeployFundMe.s.sol --rpc-url http://localhost:8545 --private-key 0xac0974bec39a17e36ba4a6b4d238ff944bacb478cbed5efcae784d7bf4f2ff80 --broadcast
```

2. To testnet (Sepolia):

```bash
forge script script/DeployFundMe.s.sol --rpc-url $SEPOLIA_RPC_URL --private-key $PRIVATE_KEY --broadcast --verify --etherscan-api-key $ETHERSCAN_API_KEY
```

### Interactions

After deployment, you can interact with the contract using the following scripts:

1. Fund the contract:

```bash
forge script script/Interactions.s.sol:FundFundMe --rpc-url $SEPOLIA_RPC_URL --private-key $PRIVATE_KEY --broadcast
```

2. Withdraw funds (only owner):

```bash
forge script script/Interactions.s.sol:WithdrawFundMe --rpc-url $SEPOLIA_RPC_URL --private-key $PRIVATE_KEY --broadcast
```

## Contract Details

The main contract `FundMe.sol` includes:

- Funding functionality with minimum amount
- Price feed integration with Chainlink
- Owner-only withdrawal
- Funding tracking per funder

## Testing

The project includes both unit tests and integration tests:

- Unit tests in `test/unit/`
- Integration tests in `test/integration/`

Tests cover:

- Funding functionality
- Withdrawal mechanics
- Owner permissions
- Price feed integration
- Multiple funders scenarios

## Acknowledgments

- [Foundry Book](https://book.getfoundry.sh/)
- [Chainlink Price Feeds](https://docs.chain.link/data-feeds/price-feeds)
- [Patrick Collins' Foundry Course](https://www.youtube.com/watch?v=sas02qSFZ74)
