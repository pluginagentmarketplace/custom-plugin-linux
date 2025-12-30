---
name: blockchain
description: Blockchain development skill - Smart contracts, DeFi, Web3, consensus
version: "1.0.0"
sasmp_version: "1.3.0"

input_schema:
  type: object
  properties:
    task: { type: string, enum: [develop, audit, deploy, optimize, integrate] }
    platform: { type: string, enum: [ethereum, solana, polygon, arbitrum, base] }
  required: [task]

output_schema:
  type: object
  properties:
    contract: { type: string }
    audit_report: { type: object }
    gas_analysis: { type: object }

retry_config:
  max_attempts: 3
  backoff: exponential

timeout_ms: 120000
---

# Blockchain Development Skill

## PURPOSE
Smart contract development, DeFi protocols, and Web3 integration.

## CORE COMPETENCIES
```
Smart Contracts:
├── Solidity (EVM)
├── Rust (Solana)
├── Move (Sui/Aptos)
├── Security patterns
└── Upgradability

DeFi Protocols:
├── AMM/DEX
├── Lending/Borrowing
├── Yield farming
├── Staking
└── Oracles (Chainlink)

Web3 Integration:
├── ethers.js / viem
├── Wallet connection
├── Transaction handling
├── Event listening
└── IPFS/Arweave
```

## CODE PATTERNS

### Solidity Contract
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/access/Ownable.sol";
import "@openzeppelin/contracts/utils/ReentrancyGuard.sol";

contract SecureVault is ReentrancyGuard, Ownable {
    mapping(address => uint256) private balances;

    event Deposited(address indexed user, uint256 amount);
    event Withdrawn(address indexed user, uint256 amount);

    function deposit() external payable nonReentrant {
        require(msg.value > 0, "Amount must be > 0");
        balances[msg.sender] += msg.value;
        emit Deposited(msg.sender, msg.value);
    }

    function withdraw(uint256 amount) external nonReentrant {
        require(balances[msg.sender] >= amount, "Insufficient balance");
        balances[msg.sender] -= amount;
        (bool success, ) = msg.sender.call{value: amount}("");
        require(success, "Transfer failed");
        emit Withdrawn(msg.sender, amount);
    }
}
```

### Web3 Integration
```typescript
import { createPublicClient, createWalletClient, http } from 'viem';
import { mainnet } from 'viem/chains';

const publicClient = createPublicClient({
  chain: mainnet,
  transport: http(),
});

// Read contract
const balance = await publicClient.readContract({
  address: contractAddress,
  abi: vaultABI,
  functionName: 'balanceOf',
  args: [userAddress],
});

// Write contract
const hash = await walletClient.writeContract({
  address: contractAddress,
  abi: vaultABI,
  functionName: 'deposit',
  value: parseEther('1'),
});
```

## SECURITY CHECKLIST
```
[ ] Reentrancy protection
[ ] Integer overflow (use 0.8+)
[ ] Access control
[ ] Input validation
[ ] Check-effects-interactions pattern
[ ] Slippage protection
[ ] Oracle manipulation resistance
[ ] Flash loan attack prevention
[ ] Upgrade security (timelock)
[ ] Emergency pause mechanism
```

## TROUBLESHOOTING

| Issue | Cause | Solution |
|-------|-------|----------|
| Reentrancy | External call before state update | Use ReentrancyGuard |
| Front-running | Public mempool | Use commit-reveal |
| Oracle manipulation | Single source | Multiple oracles, TWAP |
| High gas | Inefficient storage | Pack structs, use events |
