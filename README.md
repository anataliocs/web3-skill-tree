# Ethereum Basics in 5 Minutes


---

Almost all smart contract L1 blockchains(Solana, Ethereum L2s[Polygon, Optimism etc]) follow the account based model.  Notable exceptions include Bitcoin and Cardano with follow a UTXO model.


## **Accounts:**  [https://ethereum.org/en/developers/docs/accounts/](https://ethereum.org/en/developers/docs/accounts/)



* Externally-owned account (EOA) – controlled by anyone with the private keys
* Contract account – a smart contract deployed to the network, controlled by code. Learn about smart contracts

**TLDR;**  Wallets are EOAs.  Private key == wallet.  Smart contracts are just wallets controlled by code.


## **Transactions:**  [https://ethereum.org/en/developers/docs/transactions/](https://ethereum.org/en/developers/docs/transactions/)



* Transactions are state changes:
    * Basic:  Send Ethereum
    * Smart contract interaction:  Change data in a smart contract(Update a variable or an array)  e.g. Update array so that NFT “1” is owned by wallet xxx(Public wallet hash)
    * Contract deployments:  Publishing a smart contract so others can use

**TLDR;**  Everything on the blockchain is a transaction.  A transaction is just a data update.  


## **Blocks: ** [https://ethereum.org/en/developers/docs/blocks/](https://ethereum.org/en/developers/docs/blocks/)



* Blocks are just batches of transactions
* A block is a group of transactions every ~12s slot
* Validators check a block by checking the hash
* Magic computer science, lets you check 1 hash to verify the entire history(Merkle trees)
* Other validator attest that your validation is correct(attestations, Proof of stake) i.e. double-checking your work to keep you honest
* Block is “set in stone” after finality:  [https://ethereum.org/fil/roadmap/single-slot-finality/](https://ethereum.org/fil/roadmap/single-slot-finality/)
* Blocks are like timestamps of the state of the chain at a certain point-in-time

**TLDR;**  Blocks are groups of transactions that get verified together.  The magic of blockchain is you can verify the entire history of the chain by checking a single hash.  It keeps everyone honest.


# Advanced Ethereum


---


## **Bridges:** [https://ethereum.org/en/developers/docs/bridges/](https://ethereum.org/en/developers/docs/bridges/)



* Bridges transfer assets across chains.
* Types of bridges:
    * **Lock and mint** – Lock assets on the source chain and mint assets on the destination chain
    * **Burn and mint** – Burn assets on the source chain and mint assets on the destination chain
    * **Atomic swaps** – Swap assets on the source chain for assets on the destination chain with another party(Needs a 3rd party sometimes)
* Bridges can create additional risk and spread risk to other chains

**TLDR; ** Bridges can expand economic value to other blockchains but there is a innate risk


## **Maximal Extractable Value(MEV):  **[https://ethereum.org/en/developers/docs/mev/](https://ethereum.org/en/developers/docs/mev/)



* Validators can maximize the value from a block by transaction ordering
* **Arbitrage:**  Buy from one DEX sell to another DEX to take advantage of price differences
* **Liquidations:**  Cash out gamblers that are over-leveraged.  _I.e. Margin call speculators borrowing too much against their assets to make more bets_
* **Sandwich trading(Pump and dump in a single block):  **
    1. Pump the price
    2. Let others buy at the higher prices
    3. Sell right after
    4. Occurs within a single block(So on one can react, it happens all at once)
* MEV is good AND bad for the ecosystem depending on how evil the validator is

**TLDR;**  MEV helps optimize the DeFi Ecosystem but bad actor validators can take advantage of others


## **Oracles:**  [https://ethereum.org/en/developers/docs/oracles/](https://ethereum.org/en/developers/docs/oracles/)



* Everything in a blockchain happens in a black box, a constrained environment([EVM](https://ethereum.org/en/developers/docs/evm/)) _i.e. Smart contracts can’t natively pull info from outside the blockchain_
* Everything transaction has to be repeatable(deterministic) by every other node using the same set of data _i.e. Each node needs the same set of data to start_
* Data from outside the blockchain, stock prices, weather, etc. needs to come from an oracle
* Oracles like [chainlink](https://chain.link/) verify and make data available to smart contracts
* Smart contracts rely on Oracles for price feeds and other external data

**TLDR; ** Blockchain based smart contracts are closed systems that can’t pull data from outside the chain without oracles.  Oracles verify and make external data available to smart contracts.


## **Scaling:**  [https://ethereum.org/en/developers/docs/scaling/](https://ethereum.org/en/developers/docs/scaling/)



* **Sharding:**  Split up work so every node doesn’t have to process everything.  [https://ethereum.org/en/roadmap/danksharding/](https://ethereum.org/en/roadmap/danksharding/)
* **Layer 2 scaling:**  Have another chain process multiple transactions and batch them up into a single L1 transaction i.e. L2 Optimism processes 100 transactions and then commits it to L1 Ethereum Mainnet as a single transaction
* [Optimistic](https://ethereum.org/en/developers/docs/scaling/optimistic-rollups/) vs [ZK](https://ethereum.org/en/developers/docs/scaling/zk-rollups/) Rollups is a whole rabbit hole you can dig into.
    * Both just roll up, or batch up multiple transactions into one

**TLDR:**  There’s not enough throughput(transactions per second, TPS) for 8 billion people to use Ethereum.  There are clever ways of batching up transactions, or reducing the total amount of work to increase TPS.


# Ethereum Smart Contract Basics


---


## **Solidity:**  Smart contract language



* [https://ethereum.org/en/developers/docs/smart-contracts/languages/](https://ethereum.org/en/developers/docs/smart-contracts/languages/)
* [https://docs.soliditylang.org/en/latest/solidity-by-example.html](https://docs.soliditylang.org/en/latest/solidity-by-example.html)
* [https://medium.com/@austin_48503/%EF%B8%8Fethereum-dev-speed-run-bd72bcba6a4c](https://medium.com/@austin_48503/%EF%B8%8Fethereum-dev-speed-run-bd72bcba6a4c)

**TLDR:** Solidity is #1.  Don’t learn Vyper or anything else unless you have a good reason


## **Dev Framework:**  Compile, test and deploy smart contracts



* [Truffle](https://trufflesuite.com/)
* [Hardhat](https://hardhat.org/)
* [Foundry](https://book.getfoundry.sh/)

**TLDR:** Helps your development workflow like deploying to testnet and testing your smart contract


## **Node Provider:**  Allows you to talk to the blockchain without running your own node



* [Infura](https://www.infura.io/)
* [Alchemy](https://www.alchemy.com/)
* [Quicknode](https://www.quicknode.com/)

**TLDR:** Helps you talk to the blockchain like Goerli, Ethereum testnet, or Ethereum mainnet.  Also, helps you talk to IPFS to store files and other things


## **Base Implementations:**  Don’t start from scratch.  Use battle-tested smart contract templates as a starting point.



* OpenZeppelin is industry standard
* [ERC-20](https://docs.openzeppelin.com/contracts/4.x/erc20):  Basic token i.e. Basic Attention Token, BAT or any token on Ethereum
* [ERC-721](https://docs.openzeppelin.com/contracts/4.x/erc721) or [ERC-1155](https://docs.openzeppelin.com/contracts/4.x/erc1155):  Non-fungible Tokens, NFTs

**TLDR:** Industry standard, secure implementations of tokens and NFTs and other common contracts to build on.


## **Smart Contract Testing and Auditing:**  Test your contract for vulnerabilities so you don’t get rekt

* Manual Audits:  Have experts review your contract:  [https://www.openzeppelin.com/security-audits](https://www.openzeppelin.com/security-audits)
* Automated Tests:  Test your codes functions as intended:  [https://trufflesuite.com/docs/truffle/how-to/debug-test/write-tests-in-solidity/](https://trufflesuite.com/docs/truffle/how-to/debug-test/write-tests-in-solidity/)
* Bug Finding Competition:  Have the community compete to find bugs in your code:  [https://code4rena.com/](https://code4rena.com/)
* Fuzzing:  Automated testing of security vulnerabilities in your code:  [https://consensys.io/diligence/fuzzing/](https://consensys.io/diligence/fuzzing/)

**TLDR:  **For advanced Smart contract developers that are ready to deploy to mainnet and risk real money.


# Ethereum Smart Contract Front-end Basics


---


## Front-end UI frameworks:  Ethereum dapps, decentralized applications use the same front-end technologies as other web apps.  HTML, CSS, Javascript, [ReactJS](https://react.dev/), [Tailwind](https://tailwindcss.com/)


* There are tons of existing tutorials on how to do front-end development for building UIs if that is your focus
* Learn this first if you are a new developer


## Ethereum Client Library:  Allows your Front-end UI to talk to your wallet and the blockchain


* [https://docs.web3js.org/](https://docs.web3js.org/)
* [https://docs.ethers.org/v6/](https://docs.ethers.org/v6/)


## Wallet:  Browser plugin or mobile app that contains a browser to view dapps and also contains your private key to sign transactions


* [Metamask](https://metamask.io/)


# Decentralized finance (DeFi) Basics(Primitives)


---

Basic building blocks(financial legos) for building DeFi applications.


## Stablecoins:  [https://ethereum.org/en/stablecoins/](https://ethereum.org/en/stablecoins/)

* ERC-20 token pegged to fiat currency like USD or EURO
* Can be pegged to a basket of currencies i.e. 25% USD, 25% EURO, 25% YEN, 25% YUAN
* Provides trading pair for cryptocurrencies on DEXs i.e. ETH/USDC or ETH/DAI
* Provides access to more stable fiat for citizens of countries with high inflation _e.g. Argentina _
* Provides opportunity to earn interest/yield by loaning, providing liquidity _e.g. Loan USDC to traders that want leverage on their assets_
* Can be used with prepaid cards to directly spend crypto with a swipe e.g. Coinbase Card
* You can borrow USDC against your crypto for leverage or other DeFi opportunities in exchange for additional risk
* International transfers and remittance


### Types of Stablecoins

**Fiat-backed**

* Example:  [USDC](https://www.circle.com/en/usdc)
* 100% Backed by USD cash and Treasuries 
* Monthly audits:  [https://www.circle.com/hubfs/USDCAttestationReports/2023/2023%20USDC_Circle%20Examination%20Report%20May%202023.pdf](https://www.circle.com/hubfs/USDCAttestationReports/2023/2023%20USDC_Circle%20Examination%20Report%20May%202023.pdf)
* Centralized and run by Circle corporation

**Crypto-Collateralized**

* Example: [DAI](https://makerdao.com/en/)
* Overcollateralized i.e. if the price of ETH drops a lot there’s a big buffer that there’s still enough ETH to back the DAI
* Collateral is public domain on blockchain:  [https://daistats.com/#/](https://daistats.com/#/)
* Stats:  https://dune.com/hagaetc/maker-dao---mcd
* Decentralized DAO run by MakerDAO holders

Don’t mess with algorithmic stablecoins.  RIP TERRA & UST

## Money Markets(Liquidity Protocols):  [https://docs.aave.com/hub/](https://docs.aave.com/hub/)

* Examples:  [Aave](https://aave.com/), [Compound](https://compound.finance/)
* Allow you to deposit crypto to earn interest(yield)
* Allows you to borrow against your deposited crypto as collateral for a fee(APR)
* No credit check, pseudo anonymous, just need a wallet 
* **Example use case:  **
    * Deposit ETH
    * Borrow USDC against ETH collateral
    * Buy more ETH with USDC
    * Gain increased exposure to ETH(leverage)
    * Sell if capital increases in price to magnify gains(AND losses)
* Can pull USDC(fiat stablecoin) out to spend IRL without selling crypto collateral
* Can be integrated into other DeFi protocols
* [Variable APR](https://docs.aave.com/risk/liquidity-risk/borrow-interest-rate) changes based on total amount borrowed in ecosystem.  _I.e. as more of a asset reserve is borrowed, interest rate increases to incentivize deposits_
* If your crypto collateral drops dramatically, you may be liquidated
* **Advanced use case: ** [Flash loans](https://docs.aave.com/faq/flash-loans)


## Decentralized Exchanges(DEXs):  [https://docs.uniswap.org/concepts/overview](https://docs.uniswap.org/concepts/overview)

* Examples: [Uniswap](https://docs.uniswap.org/concepts/overview)
* Allows swaps of asset pairs without centralized order box and matching engine


Next Page: [Solidity Primitives](https://anataliocs.github.io/web3-skill-tree/solidity-primitives)
