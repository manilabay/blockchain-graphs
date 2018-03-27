# blockchain-graphs
To create ELI5 graphs (Explain Like I'm Five) for different Blockchain and DLTs projects

* [Interledger Protocol ILP](#interledger-protocol---ilp)
* [Hyperledger](#hyperledger)
* [Ethereum](#ethereum)
* [IPFS](#ipfs)

# Interledger Protocol - ILP

Status: WIP

## Architecture

![Interledger Protocol](interledger-protocol.png?raw=true "Interledger Protocol")

## Quick ELI5 explanation

### Short description function
ILP is an intermediary layer to interoperate between different Blockchain or DLTs. Interoperatibility

### Long description function
The purpose of the interledger protocol is to enable hosts to route payments through an interconnected set of ledgers. This is done by passing the payments from one interledger module to another until the destination is reached. The interledger modules reside in hosts and connectors in the interledger system. The payments are routed from one interledger module to another through individual ledgers based on the interpretation of an interledger address. Thus, a central component of the interledger protocol is the interledger address.

Graph above show Interledger Protocol Architecture (ILP). There are 4 options path for a payment from Sender to Receiver:

* a) Blue path: Using only 1 connector + 1 ledger (Apparently Cheaper). Blue path failed because Sender didn't accept the Quote in step 3.
* b) Green path: Using more than a connector + ledger (Apparently Expensive)
* c) Red path: Timeout expire or Receiver hasn't the right private key. So the asset roll back through all the connector and ledgers involved.
* d) Black path: N/A, It is not used, just to an example to show how ILP routing features works, so the black workflow is not used: Connector_D, ledger_D asset_D asset_H asset_I asset_J asset_X asset_Y asset_Z

"Apparently", Blue path seems the cheapest because less Ledger involved less fees involved, but ILP is about multi-hop payments and it could be possible than multiple chain connectors is cheaper than 1 connector due the fees and another ledger performance factors because connectors could agreed and interchange assets with another transactions in transit to reduce costs.

### Components

* Ledger: Store Records. Ledger in ILP could be decentralized(1 entity) or decentralized(n entities) blockchain or DLTs. 1 Ledger track 1 Asset. An **important Ledger feature** in ILP it can support positive or negative balances, so it could maintain assets or liabilities. Architecture above show multiple assets and liability_R.

* Connector: Normally ILP manage it as a Plugin, as it is a program to speak with different ledgers. It gets revenue when transfer from one connector to another. It creates a smart contract inside the blockchain/ledger with a timeout and a transaction agreed by 2 parties: sender and receiver. Connectors also generate quotes.

* Asset: It represents any abstract/logical value, the balance is saved in the blockchain/ledger. As usually in blockchains, assets could be used only when provide the private key. Asset and liabilities are the same but asset is unlock with owner private key and liability is unlock with counter party owner private key.

### Workflow explanation by Arrows number

1. Sender init the payment choosing asset_A as mutual asset between Sender and Receiver
2. Connector_A prepare a quote and offer to Sender
3. Sender reject the Connector_A quote
4. Connector_B confirm than Receiver hasn't Asset_B through the Ledger_B and the Receiver Public key and prepare another quote(Ledger_B) to send to another Connector in the network.
5. Connector_B request Connector_C to check the same and transfer the operation and his quote to Connector_C
6. Connector_C confirm Receiver has Asset_C checking in ledger_C by Receiver public key and send the quote for Connector_B and Connector_C to Sender
7. Sender accept the quote so the payment start
8. Connector_B write in ledger_B the info and fee
9. Connector_C write in ledger_C the info and fee
10. If receiver has the right private key and accept the payment within the time agreed, then Receiver get the Asset. Otherwise rollback operation start and the Asset return to the Sender automatically through all the red path.
11. asset_C balance is saved into Ledger_C and Receiver have access to asset_C.

## Cryptographic ILP Transaction workflow (self-explained)

![Interledger Protocol Transaction](interledger-protocol-transaction.png?raw=true "Interledger Protocol Transaction")

### Some facts
Sender choose the Asset to do the payment and accept a quote for the connector chain, once quote(and connector chain) is accepted payment start. Receiver could get the payment through asset_A or asset_C.

## ILP Q&A to research

* Could the receiver choose the asset to get the payment? I understood no, because if receiver could choose which asset to receive it could unfair due the fee is payed by the sender only.

# IPFS

Status: WIP

![IPFS](ipfs.png?raw=true "IPFS")

# Hyperledger

# Ethereum

Status: WIP

* Permissionless blockchain to access and operate in the network, thats mean Public, all is broadcast to all nodes.
* Operation-less, you don't need build and maintain infrastructure
* Consensus: PoW (Homestead version) with CPU and Memory (ASIC-proof) + PoS (Serenity version)
* Private key to lock Addresses and Smart Contracts
* Dapps development with smart contracts.
* Crypto-fuel (aka Gas) to use the blockchain to compute, transfer and storage. You use cryptocurrency Ether(ETH) to pay for gas.
* Miners are the validators

![Ethereum Architecture](ethereum-architecture.png?raw=true "Ethereum")

Basically:

* Green arrows represent sync workflow for all the public ethereum network
* Black arrows represent components whichever node has and actions could run

## cpp-ethereum

I wont't draw again the cpp-ethereum architecture as it is already designed with graphviz also here:

[Ethereum Architecture](http://ethdocs.org/en/latest/ethereum-clients/cpp-ethereum/architecture.html)

# Stellar

# Ripple

# R3 Corda

* Permissioned blockchain to access and operate in the network, thats mean Private. You build the network between all the parties you want involve, nobody else.
* With Infrastructure, you need build your node and maintain your infrastructure
* Consensus: Multi Consensus algorithm: RAFT, BFT or whichever. You can have multiple notaries with different consensus algorithms.
* Private key to lock Addresses and Smart Contracts
* CordaDapps development with smart contracts
* Cryptocurrency is not required to use the network
* There aren't miners, there are notaries
