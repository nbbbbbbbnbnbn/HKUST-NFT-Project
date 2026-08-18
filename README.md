# HKUST-NFT-Project
# Advanced AI NFT Collection

An ERC-721 smart contract built with Solidity, OpenZeppelin, and IPFS, featuring custom mint fees, maximum supply limits, withdrawal capabilities, and on-chain pseudo-randomness for NFT traits.

## Image Generation Walkthrough

### 1. Initial Idea
- **Initial Idea:** The main mascot of the NFT is based off of the playable character of a game I like called rain world.

### 2. Prompt
- **Prompt:** For my prompt I told the AI to make a character that would look like the character I like and told it to include the metaverse name and the name of the course. 

### 3. Refining
- **Refining:** After my image was generated I would give my opinions to the AI until it gave something that i felt was really good.

## Deployed Contract
- **Network:** Ethereum Sepolia Testnet
- **Contract Address:** `0x22159A25e8B939eBBDaC9fCFe8EA3B365657ABf7`

## Code Walkthrough & Features

### 1. Contract Customization & Extension
- **Mint Price & Supply:** Enforces a fixed price (`MINT_PRICE = 0.001 ether`) and caps total mints with `MAX_SUPPLY = 10`.
- **Safe Withdrawal:** Includes an `onlyOwner` function using modern low-level `.call{value: balance}("")` to safely transfer contract funds to the deployer.

### 2. On-Chain Randomness
- **Dynamic Traits:** Implements `_generateRandomScore()` using `keccak256(abi.encodePacked(block.prevrandao, block.timestamp, msg.sender, seed))` to generate a random rarity score (1–100) per token.
- **State Mapping:** Stores the generated attribute directly on-chain via `tokenRarity[tokenId]`.

### 3. IPFS Asset & Metadata Hosting
- Artwork variants and JSON metadata files are stored on IPFS via Pinata.
