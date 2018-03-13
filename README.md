# blockchain-graphs
To create ELI5 graphs (Explain Like I'm Five) for different Blockchain and DLTs projects

# Interledger Protocol - ILP

![Interledger Protocol](interledger-protocol.png?raw=true "Interledger Protocol")

## Quick ELI5 explanation

Left graph show Interledger Protocol architecture. There are 2 options path for a payment from Sender to Receiver:

* 1. Green path: Using only a connector (Cheaper)
* 2. Blue path: Using more than a connector (Expensive)

Green path is cheaper because less Ledger involved less fees involved.

Sender choose the Asset to do the payment and accept a quote for the connector chain, once quote(and connector chain) is accepted payment start.
Receiver could get the payment through asset_A or asset_C, but

Right graph: TODO

## Q&A to research

* Could the receiver choose the asset to get the payment? I understood no, because if receiver could choose which asset to receive it could unfair due the fee is payed by the sender only.
