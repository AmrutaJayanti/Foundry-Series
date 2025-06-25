# 🧪 Foundry Series — Day 2

## 🔨 Compilation with `forge build`

What *really* happens when you compile your **Smart Contracts** 🤔

### 🛠 `forge build` – What it does:

When you run: 

```bash
forge build
```

Foundry:

1. Uses the Solidity compiler (solc) under the hood.
2. Compiles everything in the `src/` folder.
3. Outputs machine-readable files in the `out/` directory.

Consider Vault.sol :

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.25;

contract Vault {
    struct Vault {
        uint256 amount; //How much ETH is deposited
        uint256 unlockTime; // When the funds can be withdrawn
    }

    mapping(address => Vault) public vaults; //Store vaults by user address

    function deposit(uint256 _unlockTime) external payable {
        require(msg.value > 0, "Must send ETH");
        require(_unlockTime > block.timestamp, "Unlock time must be in future");

        vaults[msg.sender] = Vault(msg.value, _unlockTime); //Stores it in the vaults for the caller
    }

    //Withdraw function
    function withdraw() external {
        Vault memory userVault = vaults[msg.sender];
        require(userVault.amount > 0, "No funds");
        require(block.timestamp >= userVault.unlockTime, "Too early");

        delete vaults[msg.sender];
        payable(msg.sender).transfer(userVault.amount);
    }

    function getVault(address user) external view returns (Vault memory) {
        return vaults[user];
    }
}
```

📂 `out/` Directory – What’s Inside?

```
out/
└── Vault.sol/
    ├── Vault.json         ⬅️ Main build artifact
    └── Vault.metadata.json
```

`Vault.json` contains all the important info:

- `abi` : **Application Binary Interface** – Tells external apps (like scripts or frontends) how to interact with your contract (functions, events, inputs/outputs).
- `bytecode` : **Hex code** deployed to Ethereum Blockchain
- `ast` : **Abstract Syntax Tree** – A tree-like structure that represents your contract’s source code for analysis or tooling.
- `methodIdentifiers` : Function names and their function selectors (used for calling them via ABI).

### 🧪 Sample Code Snippet From ABI
Here’s what a simple function looks like in ABI:

```
{
  "inputs": [{"internalType": "uint256", "name": "_unlockTime", "type": "uint256"}],
  "name": "deposit",
  "outputs": [],
  "stateMutability": "payable",
  "type": "function"
}
```
