# HKUST-NFT-Project
# Advanced AI NFT Collection

An ERC-721 smart contract built with Solidity, OpenZeppelin, and IPFS, featuring custom mint fees, maximum supply limits, withdrawal capabilities, and on-chain pseudo-randomness for NFT traits.

## Deployed Contract
- **Network:** Ethereum Sepolia Testnet
- **Contract Address:** `0xdAc094537C3c2e5e333178CC8D95A955db333a2d`

## Code Walkthrough & Features

### 1. Contract Customization & Extension
- **Mint Price & Supply:** Enforces a fixed price (`MINT_PRICE = 0.001 ether`) and caps total mints with `MAX_SUPPLY = 10`.
- **Safe Withdrawal:** Includes an `onlyOwner` function using modern low-level `.call{value: balance}("")` to safely transfer contract funds to the deployer.

### 2. On-Chain Randomness
- **Dynamic Traits:** Implements `_generateRandomScore()` using `keccak256(abi.encodePacked(block.prevrandao, block.timestamp, msg.sender, seed))` to generate a random rarity score (1–100) per token.
- **State Mapping:** Stores the generated attribute directly on-chain via `tokenRarity[tokenId]`.

### 3. IPFS Asset & Metadata Hosting
- Artwork variants and JSON metadata files are stored on IPFS via Pinata.
