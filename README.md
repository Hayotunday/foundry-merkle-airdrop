# Foundry Merkle Airdrop

A Foundry-based Merkle airdrop prototype that demonstrates how token distributions can be validated using Merkle proofs and signed claim data. The project is designed to show a secure way to distribute tokens to eligible recipients without exposing an unnecessary amount of data or requiring a centralized permission layer.

## What the product does
This repository implements an airdrop flow where eligible users can claim tokens only if they provide proof that they are included in the Merkle tree and present valid signed claim data. The contract verifies both the proof and the signature before transferring tokens.

## The problem it solves
Airdrops often need to be secure, verifiable, and efficient. The challenge is to prove that only eligible claimants receive funds while preventing duplicate claims and unauthorized transfers. This project addresses that through Merkle proofs and signed claims.

## My specific contribution
I implemented the airdrop contract, token setup, Merkle verification logic, and deployment scripts used to mint and distribute tokens in a Foundry workflow.

## Architecture
The repo contains:

- `src/MerkleAirdrop.sol` — main airdrop contract
- `src/BagelToken.sol` — ERC20 token for airdrop distribution
- `script/DeployMerkleAirdrop.s.sol` — deployment flow
- `script/GenerateInput.s.sol` and related scripts — proof generation helpers
- `test/MerkleAirdropTest.t.sol` — validation tests
- `lib/` — dependency libraries

## Technologies
- Solidity
- Foundry
- Merkle proofs
- OpenZeppelin token and cryptographic utilities
- EIP-712 typed data signing
- ERC20 distribution patterns

## Important technical decisions
- Merkle proofs are used to verify claim eligibility without storing huge claim arrays on-chain.
- EIP-712 typed data is used to validate signed claim payloads.
- Claim tracking prevents the same address from claiming multiple times.
- The project uses custom errors to clearly expose invalid-proof, invalid-signature, and duplicate-claim conditions.

## Key features
- Merkle-based token claim verification
- Signature-based claim validation
- One-time claim protection per address
- ERC20 token mint/distribution workflow
- Easily extendable proof-generation scripts for airdrops

## Screenshots
No screenshots are included.

## Live demo
No live deployment is included in the repo.

## Challenges and solutions
The main challenge was ensuring that the claim process is both secure and deterministic. This was addressed by validating both the presence of the claimant in the Merkle tree and the authenticity of the signed claim data before transferring tokens.

The project also needed to prevent duplicate claims and protect the contract from invalid proof data. That was solved with explicit state tracking and validation guards.

## Setup instructions
```bash
# Install Foundry
curl -L https://foundry.paradigm.xyz | bash
foundryup

# Clone
git clone https://github.com/Hayotunday/foundry-merkle-airdrop.git
cd foundry-merkle-airdrop

# Install dependencies
forge install

# Build
forge build

# Run tests
forge test

# Optional
forge fmt
forge snapshot
```

## What makes the project technically interesting
This project is technically interesting because it combines cryptographic verification with token distribution logic. Merkle proofs and signed messages are core blockchain techniques that allow claims to be verified efficiently while preserving security and minimizing on-chain overhead.

## Project status
This repo is a learning and prototyping project for Merkle-based token distribution and signature validation.

## License
Check the repository license file for the exact license terms.
