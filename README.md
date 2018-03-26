# blockchain-graphs
To create ELI5 graphs (Explain Like I'm Five) for different Blockchain and DLTs projects

[Interledger Protocol ILP](#interledger-protocol---ilp)
[Hyperledger](#Hyperledger)
[IPFS](#IPFS)

# Interledger Protocol - ILP

Status: WIP

![Interledger Protocol](interledger-protocol.png?raw=true "Interledger Protocol")

## Quick ELI5 explanation

Left graph show Interledger Protocol architecture. There are 4 options path for a payment from Sender to Receiver:

* a) Blue path: Using only 1 connector + 1 ledger (Apparently Cheaper). Blue path failed because Sender didn't accept the Quote in step 3.
* b) Green path: Using more than a connector + ledger (Apparently Expensive)
* c) Red path: Receiver reject the payment or hasn't the right private key. So the asset roll back through all the connector and ledgers involved.
* d) Black path: N/A, It is not used, just to an example to show how ILP routing features works, so the black workflow is not used: Connector_D, ledger_D asset_D asset_H asset_I asset_J asset_X asset_Y asset_Z

"Apparently", Blue path seems the cheapest because less Ledger involved less fees involved, but It could be possible than multiple chain connectors is cheaper than 1 connector due the fees and another ledger performance factors.

### Components

* Ledger: Store Records. Ledger in ILP could be decentralized(1 entity) or decentralized(n entities) blockchain or DLTs. 1 Ledger track 1 Asset. An **important Ledger feature** in ILP it can support positive or negative balances, so it could maintain assets or liabilities.

* Connector:



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
10. If receiver has the right private key and accept the payment, receiver get the Asset. Otherwise rollback operation start and the Asset return to the Sender through all the red path.

### Some facts
Sender choose the Asset to do the payment and accept a quote for the connector chain, once quote(and connector chain) is accepted payment start. Receiver could get the payment through asset_A or asset_C.

Right graph: TODO

## ILP Q&A to research

* Could the receiver choose the asset to get the payment? I understood no, because if receiver could choose which asset to receive it could unfair due the fee is payed by the sender only.

# IPFS

Status: WIP

![IPFS](ipfs.png?raw=true "IPFS")

# Ethereum

# Stellar

# Ripple

# Hyperledger

# R3 Corda

#
