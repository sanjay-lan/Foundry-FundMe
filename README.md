# FundMe Smart Contract

## Overview
The `FundMe` contract is a decentralized crowdfunding platform that allows users to contribute funds and enables the contract owner to withdraw the collected balance. It uses Chainlink's price feeds to ensure the contributed amount meets a minimum USD threshold.

---

## Features
- **Decentralized Funding:** Users can send Ether to the contract to participate in funding.
- **Price Conversion:** Ensures the minimum contribution meets a specified USD value using Chainlink price feeds.
- **Owner-only Withdrawal:** Only the contract owner can withdraw the funds.
- **Gas Optimization:** Includes efficient storage practices like immutable and constant variables.
- **Custom Errors:** Uses custom errors for gas-efficient error handling.
- **Fallback Functions:** Handles Ether sent directly to the contract.

---

## Prerequisites
1. **Solidity Version:** ^0.8.18
2. **Dependencies:**
   - `chainlink-brownie-contracts` for price feed integration.
   - A deployed Chainlink Price Feed contract for ETH/USD conversion.

---

## Deployment
### Constructor
The contract constructor requires the address of a Chainlink price feed for deployment.
```solidity
constructor(address priceFeed) {
    i_owner = msg.sender;
    s_priceFeed = AggregatorV3Interface(priceFeed);
}
