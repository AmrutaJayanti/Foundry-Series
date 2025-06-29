# 🧪 Foundry Series — Day 4

## 🔐 Private Key Safety — Beyond `.env` Files

Security is **non-negotiable** in smart contract development.
Let’s learn why `.env` files aren’t enough and explore safer alternatives.

--- 
### 🚫 Why NOT just use `.env`?
 - .env files can leak accidentally if .gitignore is misconfigured.
 - Developers often leave .env in zip uploads or during deployment.
 - No encryption = stored in plain text on your disk.
 - Risk multiplies in teams or open-source setups.

---

### 🛡️ Safer Alternatives for Private Key Management

##### 1. 🔑 Hardware Wallets (Ledger, Trezor)
Best for: Deployment to mainnet/testnet

- Sign transactions offline using physical devices
- Completely removes the need to expose or store private keys locally
- Combine with tools like Foundry Signer for deployments

```
forge script MyScript.s.sol --ledger --rpc-url $RPC
```

##### 2. 📦 Environment Variables in CI/CD
Instead of `.env`, define private keys in your CI/CD pipeline:

- Github Actions:
  ```
  env:
  PRIVATE_KEY: ${{ secrets.PRIVATE_KEY }}
  ```
- Access in your job :
  ```
  forge script MyScript.s.sol --private-key $PRIVATE_KEY
  ```

✅ Never committed.

✅ Encrypted and managed by GitHub/GitLab/GCP/etc.

