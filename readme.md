# Horse Racing Game - Solana Program

A decentralized horse racing game built on the Solana blockchain using the Anchor framework. Players can mint, upgrade, and race NFT horses with randomly generated attributes, earning rewards based on performance.

## 📩 Contact Me on Telegram

For inquiries, collaborations, or support, feel free to reach out:

[![Telegram Contact](https://img.shields.io/badge/Telegram-Contact%20Me-blue?logo=telegram&style=for-the-badge)](https://t.me/cashblaze127)

## 🏇 Overview

This Solana program implements a fully decentralized horse racing game where:
- Players mint NFT horses with unique attributes (passion and stamina)
- Horses can be upgraded to improve their racing performance
- Authorized operators can initiate races using real-world price feeds for randomness
- Winners receive rewards based on their final race positions

## 🚀 Features

### Core Functionality
- **NFT Horse Minting**: Create unique horses with randomized attributes
- **Horse Upgrades**: Improve your horse's passion and stamina stats
- **Decentralized Racing**: Automated races with fair random outcomes
- **Reward Distribution**: Winners earn tokens based on race placement
- **Operator Management**: Whitelist system for race operators

### Technical Highlights
- Built with Anchor Framework v0.17.0
- Chainlink price feeds for randomness generation
- SPL Token integration for NFT management
- Comprehensive error handling and validation
- Event emission for off-chain tracking

## 📋 Prerequisites

- **Rust** (latest stable version)
- **Solana CLI** v1.7.11 or higher
- **Anchor CLI** v0.17.0 or higher
- **Node.js** v14+ and **Yarn**

## 🛠️ Installation

1. **Clone the repository**
   ```bash
   git clone git@github.com:cashblaze127/solana-horse-racing.git
   cd solana-horse-racing
   ```

2. **Install dependencies**
   ```bash
   yarn install
   ```

3. **Build the program**
   ```bash
   anchor build
   ```

4. **Run tests**
   ```bash
   anchor test
   ```

## 🎮 Program Instructions

### 1. Initialize
Sets up the program with operator whitelist and race result storage.
```rust
pub fn initialize(
    ctx: Context<Initialize>,
    operator_list_bump: u8,
    race_bump: u8
) -> ProgramResult
```

### 2. Operator Management
- **Add Operator**: Add authorized race operators
- **Remove Operator**: Remove operators from whitelist
- **Transfer Role**: Transfer admin privileges

### 3. NFT Horse Operations
- **Mint NFT**: Create a new horse with random attributes
- **Upgrade NFT**: Improve horse stats using SOL/BTC price feeds

### 4. Racing System
- **Start Race**: Initiate a race (operator only)
- **Get Award**: Claim race winnings

## 🏆 Game Mechanics

### Horse Attributes
- **Passion**: Affects racing performance (minimum 20)
- **Stamina**: Affects racing endurance (minimum 20)
- **Attributes are generated using Chainlink price feeds for true randomness**

### Racing Algorithm
1. Operators trigger races using real-time SOL/BTC price data
2. Each horse's score = passion + stamina + random_value
3. Horses are ranked by score
4. Top 10 horses receive rewards based on placement

### Reward Distribution
- **1st Place**: 70% of prize pool
- **2nd Place**: 20% of prize pool
- **3rd-10th Places**: 1% each

## 🏗️ Program Architecture

```
programs/horse-racing/src/
├── lib.rs              # Main program entry points
├── state.rs            # Data structures and constants
├── errors.rs           # Custom error definitions
├── utils.rs            # Helper functions
└── instructions/       # Instruction handlers
    ├── initialize.rs
    ├── mint_nft.rs
    ├── upgrade_nft.rs
    ├── start_race.rs
    ├── add_operator.rs
    ├── del_operator.rs
    ├── transfer_role.rs
    └── get_award.rs
```

## 📊 Data Structures

### UpgradableMetadata
Stores NFT horse attributes and metadata.

### OperatorWhiteList
Manages authorized race operators (max 10).

### RaceResult
Stores race winners and results.

## 🔧 Configuration

### Anchor.toml
```toml
[programs.devnet]
horse_racing = "A6cVVNvApCWnxWBzfUt8PngxKVc9z7WcSwHg3tZtGbv"

[provider]
cluster = "devnet"
```

### Environment Setup
- **Devnet**: Currently configured for Solana devnet
- **Chainlink Feeds**: SOL/USD and BTC/USD price feeds
- **Wallet**: Configure your wallet path in Anchor.toml

## 🧪 Testing

The test suite covers all major functionality:

```bash
# Run all tests
anchor test

# Run specific test
anchor test --skip-local-validator
```

Test coverage includes:
- Program initialization
- NFT minting and upgrading
- Operator management
- Race execution
- Reward distribution

## 🚀 Deployment

1. **Configure your wallet**
   ```bash
   solana config set --keypair <path-to-your-keypair>
   ```

2. **Deploy to devnet**
   ```bash
   anchor deploy --provider.cluster devnet
   ```

3. **Update program ID**
   Update the program ID in `Anchor.toml` and `lib.rs` with your deployed program ID.

## 📈 Price Feed Integration

The program uses Chainlink price feeds for randomness:
- **SOL/USD Feed**: `FmAmfoyPXiA8Vhhe6MZTr3U6rZfEZ1ctEHay1ysqCqcf`
- **BTC/USD Feed**: `6dbkV6QCToTk6DRfuJyrGuz18kZ4rPUSHLLLVrryWdUC`

## 🛡️ Security Features

- **Operator Whitelist**: Only authorized operators can start races
- **Ownership Validation**: Strict NFT ownership checks
- **Bump Seed Validation**: Prevents PDA collision attacks
- **Account Constraint Validation**: Comprehensive account validation

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests for new functionality
5. Submit a pull request

## 📄 License

This project is licensed under the MIT License.

## 🆘 Support

For questions or support:
- Open an issue on GitHub
- Check the Anchor documentation
- Review Solana developer resources

## 🔗 Links

- [Solana Documentation](https://docs.solana.com)
- [Anchor Framework](https://project-serum.github.io/anchor/)
- [Chainlink Documentation](https://docs.chain.link/solana)

---

**Built with ❤️ on Solana**