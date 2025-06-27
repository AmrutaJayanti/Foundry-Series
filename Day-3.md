# 🧪 Foundry Series — Day 3
## 🚀 Deploying Smart Contracts using Anvil + Forge

### 🌐 What is Anvil?
Anvil is a fast local Ethereum RPC node, similar to Ganache but written in Rust (like Foundry). It simulates a blockchain environment and gives you test accounts with ETH to deploy and interact with contracts **locally**.

*Think of it as your personal Ethereum sandbox. No gas, no waiting, no mainnet risk.*

##### 📦 Step 1: Start Anvil

In a terminal,run:

```
anvil
```
You'll see :

- RPC URL : `http://127.0.0.1:8545`
- Private keys and account addresses

##### 🛠️ Step 2: Create a Simple Contract
Inside `src/Counter.sol` (A simple example file):

```
// SPDX-License-Identifier: UNLICENSED
pragma solidity ^0.8.20;

contract Counter {
    uint public count;

    function increment() public {
        count += 1;
    }
}
```

##### 📜 Step 3: Write the Deployment Script
Inside `script/Deploy.s.sol`:

```
// SPDX-License-Identifier: UNLICENSED
pragma solidity ^0.8.20;

import "forge-std/Script.sol";
import "../src/Counter.sol";

contract DeployScript is Script {
    function run() external {
        vm.startBroadcast();
        new Counter();
        vm.stopBroadcast();
    }
}
```

##### ⚙️ Step 4: Build the Contract

```
forge build
```

##### 🚀 Step 5: Deploy to Anvil using Forge

Open another terminal and run:

```
forge script script/Deploy.s.sol:DeployScript --rpc-url http://127.0.0.1:8545 --broadcast
```
Explanation:

- `script/Deploy.s.sol:DeployScript` → Your script path and contract name.
- `--rpc-url` → Anvil’s endpoint.
- `--broadcast` → Actually sends the transaction to the local chain.
