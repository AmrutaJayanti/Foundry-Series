
# 🧪 Day 1: What is Foundry? And How I Started My First Smart Contract Project

📅 This is Day 1 of my journey to learn smart contract development using **Foundry** — a fast, Solidity-native toolkit for Ethereum development.

---

## 🧠 What is Foundry?

Foundry is a **smart contract development toolkit** built for Ethereum.  
It's made by [Paradigm](https://github.com/foundry-rs/foundry) and is known for being:

- ✅ Extremely fast (written in Rust)  
- ✅ Easy to use (command-line based)  
- ✅ Native to Solidity (you write tests *in Solidity*)  
- ✅ Fully open-source and modern

Most people use Hardhat (JavaScript-based), but Foundry lets you stay focused in Solidity — no JS needed.

---

## ✅ Why I Chose Foundry

- I’m new to smart contracts and wanted to learn **cleanly, without mixing JS**  
- Foundry is being used by major DeFi protocols like Aave, Optimism, Uniswap  
- I want to write **real, testable contracts** and build confidence from day 1  
- I’ll learn faster by **building in public**

---

## ⚙️ Step-by-Step: Installing Foundry

Here’s how I installed Foundry and created my first project 👇

### 1. Install Foundry

```bash
curl -L https://foundry.paradigm.xyz | bash
foundryup
````

> ✅ This installs `forge` (for testing), `cast` (for interacting), and `anvil` (a local Ethereum node).

---

### 2. Create a New Project

```bash
forge init my-first-foundry-project
cd my-first-foundry-project
```

This gives you a folder like this:

```
my-first-foundry-project/
├── foundry.toml   # Config file
├── src/           # Where you write contracts
├── script/        # For deployment scripts
└── test/          # For Solidity test files
```



## 📘 What I Learned Today

* What Foundry is
* Why it’s useful
* How to install it
* How the project structure works
