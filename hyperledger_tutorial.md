Hyperledger video series by Ivan Vankov - https://www.youtube.com/playlist?list=PLjsqymUqgpSRXC9ywNIVUUoGXelQa4olO

**Videos 1, 2 & 3 give an overview, okay to rewatch**

# v1
- Solves the problem of trust between patries that don't trust each other. This allows us to change the business process to an efficient one, w/o middlemen and w/ security 

- Members of hyperledger - ch their projects

# v2
- Tokens can be implemented - w/o mining

- But has blockchain props - transaction ordering, ...

- 1/2 Million tranasactions/sec (1000 trans/sec in ethereum)

- You can make Hyperledger as public as you want.

- Not vulanerable to 51% attack(since there's no mining)

# v3
- 0:10 Real life scenario
    - Problem can be solved with 3rd party. Third party is reposible for comm., integrity. But requires a lot of money & a 3rd party which all can trust to safeguard the integrity. ( I think a lot of money is needed, because it must be greater than any bribes the one single org. can give)

- A business process is decided & a SC is created.

- *Try to relate this to your project*

# v4 (Some details missed, go through again(fast))
- up till 2:00, resources
## Components
1. fabric ca
    - every operation must be signed with a certificate. Operations include to update ledger, take data.
    - up till 8:00, unimp. info
    - Can chain many together to increase security.
2. Peer
    - Stores the ledger.
    - Need more than 1 peer in production environment.
    - Request from SDK is sent to peer.
    - 1 peer may be part of multiple channels. Channels are inside the peer(code-wise).
    - All peers find each other & synchronize automatically. *Add more peers to increase throughput*.
3. Ordering Service
    - Heart of consensus algo.
    - Before anything is commited to the ledger, it must pass through the ordering service. Then it is passed to peers to be added to ledger.
    - They create the blocks in the chain. Decides the order of transactions(operations) in the block.
    - Solo Ordered - for testing & debugging.(low throughput)
    - Apache Kafka based Ordered - production.
    - Throughput can be increased by adjusting config.(Kafka can reach 1000s of transactions/min?)

# v5 Channels - main way for data isolation
- Can be thought of a separate instance of fabric. A ledger is inside a channel.
- Every channel is independent. A peer may be a part of mulitple channels.
- n peers can be added to a channel. Hence, many-to-many mapping.
- every single party must agree to let a party join.

# v6 Chaincode
- SDK makes a transactions, it is sent to peer, and peer executes the chaincode.
- Responsibility: Only thing that can read & update ledger data.
- Flexible: Can use external libraries, data from certificate(e.g-role of that user), parameters passed.
- Contains business logic.
- Goes through - https://hyperledger-fabric.readthedocs.io/en/release-1.3/chaincode4ade.html?highlight=chaincode%20for%20developers - mentions some functions
### Using chaincode
- Chaincode must first be `installed` and then `instantiated`.
- Installation of the chaincode in all peers in the channel, can be done using the SDK.
- During intantiation, the container will make all the connections, security verification, after which the chaincode is ready for use.
- Policy:
    - A policy needs to be provided before instantiation. 1 policy per chaincode.
    - Policy determines who verifies the operation before adding it to the ledger.
    - e.g- Any member or org1, any of org2, any of org3 to verify that the operation is valid.
    - What it verifies: Checks if security, certificate attributes, provenance is valid.
- Haven't finished watching video...
    