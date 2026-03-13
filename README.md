# Pet Shop — Truffle Suite DApp

A decentralized pet adoption application built with the [Truffle Suite](https://trufflesuite.com/) tutorial. Users can browse 16 pets and adopt them via a smart contract on an Ethereum blockchain, with all adoptions recorded on-chain.

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Smart contract | Solidity `^0.8.0` |
| Framework | Truffle Suite |
| Local blockchain | Ganache (port `7545`) |
| Frontend | HTML · jQuery · Bootstrap |
| Web3 bridge | `web3.js` · `@truffle/contract` |
| Dev server | `lite-server` |

## Prerequisites

- [Node.js](https://nodejs.org/) (v14+)
- [Truffle](https://trufflesuite.com/docs/truffle/how-to/install/) — `npm install -g truffle`
- [Ganache](https://trufflesuite.com/ganache/) running on `http://127.0.0.1:7545`
- [MetaMask](https://metamask.io/) browser extension connected to Ganache

## Getting Started

### 1. Install dependencies

```bash
npm install
```

### 2. Start Ganache

Open Ganache and start a workspace (or quickstart). Ensure it runs on port **7545**.

### 3. Compile & migrate contracts

```bash
truffle compile
truffle migrate
```

### 4. Connect MetaMask to Ganache

1. In MetaMask, add a custom network: `http://127.0.0.1:7545`, Chain ID `1337`.
2. Import one of the Ganache accounts using its private key.

### 5. Run the frontend

```bash
npm run dev
```

The app opens at `http://localhost:3000`.

## Smart Contract

**`contracts/Adoption.sol`**

```solidity
address[16] public adopters;

function adopt(uint petId) public returns (uint)
function getAdopters() public view returns (address[16] memory)
```

- `adopt(petId)` — records `msg.sender` as the adopter of pet `petId` (0–15).
- `getAdopters()` — returns the full adopters array so the UI can mark already-adopted pets.

## Running Tests

```bash
truffle test
```

Tests are located in `test/` and cover both Solidity (`TestAdoption.sol`) and JavaScript (`testAdoption.test.js`).

## Project Structure

```
pet-shop/
├── contracts/          # Solidity smart contracts
├── migrations/         # Truffle deployment scripts
├── src/
│   ├── index.html      # Frontend UI
│   ├── pets.json       # Pet data
│   └── js/app.js       # Web3 + contract interaction logic
├── test/               # Solidity & JS tests
├── truffle-config.js   # Truffle network & compiler config
└── bs-config.json      # lite-server config
```

## License

MIT
