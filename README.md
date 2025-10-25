# CeloRefer - Decentralized Referral System on Celo

## Overview

CeloRefer is a comprehensive, blockchain-based referral and reputation system built on the Celo blockchain. It enables applications to implement gamified referral programs with multi-level rewards, reputation NFTs, quests, seasonal competitions, and white-label partner integrations.

## What is CeloRefer?

CeloRefer is a **smart contract infrastructure** combined with a **TypeScript SDK** that allows developers to:
- Build viral growth loops with incentivized referrals
- Track and reward user actions across their dApps
- Create gamified experiences with quests and seasonal competitions
- Issue soulbound reputation NFTs to users
- Manage tiered reward systems with dynamic rates

## Key Components

### 1. Smart Contracts

#### CeloReferEnhanced.sol
The main referral system contract that handles:
- User registration with referral codes
- Two-level referral tree (direct referrer + parent referrer)
- Dynamic reward distribution based on badge tiers
- Quest system for milestone achievements
- Seasonal competitions with prize pools
- Partner authorization and platform fee management
- White-label subscription tiers

#### ReputationNFT.sol
A soulbound (non-transferable) NFT contract that:
- Mints unique reputation NFTs for users
- Represents on-chain reputation and achievement
- Cannot be transferred (soulbound token)
- Provides dynamic metadata based on user stats

#### DemoDApp.sol
Example integration contract demonstrating:
- Staking cUSD tokens
- Automatic referral registration on first action
- Integration with CeloRefer reward distribution

### 2. CeloRefer SDK

A TypeScript SDK built with **viem** that provides:
- Easy integration with CeloRefer contracts
- Type-safe contract interactions
- Comprehensive API for all contract features
- Support for read and write operations
- Built for modern web3 development

## Core Features

### 🎯 Multi-Level Referral System

**Two-tier referral tree:**
- **Level 1 (Direct Referrer)**: Earns rewards when their direct referrals perform actions
- **Level 2 (Parent Referrer)**: Earns rewards from their referrals' referrals

**Dynamic reward rates based on badge tier:**
- 🥉 **Bronze** (0-4 referrals): 5% + 2%
- 🥈 **Silver** (5-14 referrals): 10% + 4%
- 🥇 **Gold** (15-49 referrals): 15% + 6%
- 💎 **Platinum** (50+ referrals): 20% + 8%

### 🏅 Badge & Reputation System

Users earn badges based on their referral performance:
- Badges unlock higher reward rates
- Badge tier displayed in reputation NFTs
- Visual representation of user achievement
- Gamification encourages viral growth

### 🎮 Quest System

Create milestone-based challenges:
- Set target referral counts
- Offer cUSD rewards for completion
- Track user progress automatically
- Claim rewards on completion
- Drive specific user behaviors

### 🏆 Seasonal Competitions

Run time-bound competitions:
- Define season duration and prize pool
- Track user performance during season
- Distribute rewards to top performers
- Create urgency and engagement spikes
- Build community around leaderboards

### 💎 Reputation NFTs (Soulbound)

Mint on-chain reputation badges:
- Unique NFT per user (soulbound - cannot be transferred)
- Dynamic metadata reflecting current stats
- Visual representation of achievements
- Portable reputation across ecosystem
- Proof of engagement and influence

### 🤝 Partner Integration

White-label support for dApps:
- Authorize partner contracts to record actions
- Platform fee system (default 15%)
- Tiered subscription model (Free, Basic, Pro, Enterprise)
- Customization levels based on tier
- Revenue sharing through fees

### 📊 Leaderboards & Analytics

Track ecosystem performance:
- Global user rankings
- Referral counts and earnings
- Contract statistics
- Season-specific leaderboards
- User quest progress

## How It Works

### For Users

1. **Register**: Sign up with a referral code or as genesis user
2. **Get Your Code**: Receive a unique referral code
3. **Share**: Invite friends using your referral link
4. **Earn**: Receive rewards when referrals perform actions
5. **Level Up**: Earn badges as you refer more users
6. **Compete**: Participate in quests and seasonal competitions
7. **Collect**: Mint your reputation NFT

### For Developers/Partners

1. **Deploy/Connect**: Deploy contracts or connect to existing system
2. **Integrate SDK**: Install and initialize CeloRefer SDK
3. **Authorize**: Get your dApp authorized as a partner
4. **Record Actions**: Call `recordAction()` when users perform valuable actions
5. **Automatic Rewards**: System automatically distributes rewards to referrers
6. **Customize**: Create custom quests, seasons, and branding

### For Platform Owners

1. **Manage Partners**: Authorize/deauthorize partner dApps
2. **Set Fees**: Configure platform fee percentage
3. **Create Quests**: Design milestone challenges with rewards
4. **Run Seasons**: Launch time-bound competitions
5. **Collect Fees**: Receive platform fees in treasury
6. **Monitor Growth**: Track ecosystem metrics

## Smart Contract Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                     CeloReferEnhanced                       │
│  ┌───────────────────────────────────────────────────────┐  │
│  │  • User Registration & Referral Tree                  │  │
│  │  • Dynamic Reward Distribution (tiered)               │  │
│  │  • Quest System                                       │  │
│  │  • Seasonal Competitions                              │  │
│  │  │  • Badge Tier Management                            │  │
│  │  • Platform Fee Collection                            │  │
│  │  • Partner Authorization                              │  │
│  └───────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────┘
                            │
            ┌───────────────┴───────────────┐
            │                               │
┌───────────▼─────────────┐     ┌──────────▼───────────┐
│   ReputationNFT.sol     │     │   Partner dApps      │
│  • Soulbound NFT        │     │  (e.g., DemoDApp)    │
│  • User Reputation      │     │  • Stake/Action      │
│  • Dynamic Metadata     │     │  • Call recordAction │
│  • Non-transferable     │     │  • Reward Users      │
└─────────────────────────┘     └──────────────────────┘
```

## Use Cases

### 1. DeFi Protocols
- Reward users who bring liquidity providers
- Incentivize protocol adoption
- Build network effects

### 2. NFT Marketplaces
- Reward collectors who onboard creators
- Incentivize trading volume
- Grow user base virally

### 3. Gaming Platforms
- Reward players who recruit teammates
- Build guilds and communities
- Increase retention through social connections

### 4. Social dApps
- Incentivize content creators to onboard followers
- Reward community builders
- Create viral growth loops

### 5. Education Platforms
- Reward students who bring study groups
- Incentivize course completions
- Build learning communities

## Token Economics

### Reward Distribution
For every action worth **100 cUSD**:
1. **Platform Fee**: 15 cUSD (15%) → Treasury
2. **Remaining**: 85 cUSD → Referrer Rewards

**Example (Bronze Tier User):**
- Direct Referrer (Level 1): 85 × 5% = 4.25 cUSD
- Parent Referrer (Level 2): 85 × 2% = 1.7 cUSD
- Platform keeps: 15 cUSD
- User/Partner keeps: ~79.05 cUSD

**Example (Platinum Tier User):**
- Direct Referrer (Level 1): 85 × 20% = 17 cUSD
- Parent Referrer (Level 2): 85 × 8% = 6.8 cUSD
- Platform keeps: 15 cUSD
- User/Partner keeps: ~61.2 cUSD

### Sustainability Model
- Platform fees fund ecosystem development
- Quest rewards drive user engagement
- Season prize pools create competition
- Partner subscriptions for white-label features
- NFT minting fees (optional)

## Benefits

### For Users
✅ Earn passive income from referrals  
✅ Unlock higher tiers and better rewards  
✅ Compete in seasonal challenges  
✅ Build on-chain reputation  
✅ Receive soulbound NFT badges  

### For Developers
✅ Ready-to-use referral infrastructure  
✅ No need to build from scratch  
✅ Type-safe SDK with TypeScript  
✅ Customizable quest and season systems  
✅ White-label support  

### For Platforms
✅ Viral growth mechanism  
✅ Sustainable revenue model (platform fees)  
✅ Gamification increases engagement  
✅ On-chain reputation system  
✅ Partner ecosystem management  

## Technology Stack

- **Blockchain**: Celo (EVM-compatible)
- **Smart Contracts**: Solidity ^0.8.20
- **Framework**: OpenZeppelin contracts
- **SDK**: TypeScript + viem
- **Token Standard**: ERC-20 (cUSD), ERC-721 (NFT)

## Security Features

- ✅ ReentrancyGuard on all state-changing functions
- ✅ Ownable access control
- ✅ Input validation and require statements
- ✅ Soulbound NFTs prevent reputation trading
- ✅ Partner authorization system
- ✅ Emergency withdrawal for owner

## Getting Started

### For Developers
```bash
npm install @celorefer/sdk
```

```typescript
import { CeloReferSDK } from '@celorefer/sdk';
import { celoAlfajores } from 'viem/chains';

const sdk = CeloReferSDK.create(celoAlfajores, walletClient);

// Register a user
await sdk.registerUser('REFERRAL_CODE');

// Check user stats
const userInfo = await sdk.getUserInfo(userAddress);

// Record an action (for partners)
await sdk.recordAction(userAddress, actionValue);
```

See [API Documentation](./api-reference/introduction) for complete API documentation.

## Roadmap

### Phase 1: Core System ✅
- Multi-level referral tree
- Dynamic reward rates
- Badge tier system
- Basic SDK

### Phase 2: Gamification ✅
- Quest system
- Seasonal competitions
- Reputation NFTs
- Leaderboards

### Phase 3: Enterprise (In Progress)
- Advanced white-label customization
- Cross-chain support
- Subgraph for efficient querying
- Dashboard for analytics

### Phase 4: Ecosystem
- Partner marketplace
- Reputation portability
- Composable quests
- DAO governance

## Community & Support

- **Documentation**: See API docs for integration guide
- **Examples**: Check `/examples` folder in SDK package
- **Issues**: Report bugs via GitHub Issues
- **Discussions**: Community forums coming soon

## License

MIT License - see LICENSE file for details

---

**Built with ❤️ on Celo blockchain**