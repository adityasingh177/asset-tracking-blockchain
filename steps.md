Organisation Mapping for Hyperledger Fabric

The Reliance group has multiple companies working under its umbrella, 
and we are going to set up a blockchain solution between these companies to track the 
sharing of assets and products. We are going to set up the Hyperledger Fabric chain between these industries:
Reliance Infrastructure , Reliance Power , Reliance Communications , Reliance Entertainment , Reliance Capital


All the companies mentioned above will act as organisations for the case study.
The following model will define an organisation in our network:


Organisation

Name: 
The name of the organisation is retained in the original form.

Domain: 
The domain of the organisation is maintained as 
<function of the company>.reliance-network.com. 
(For example, Reliance power has its domain name as power.reliance-network.com)

Peers: 
Each organisation has two peers each, which helps maintain the network
the peers will be of one single type.
Note: These peers should have the ability to act either as a "client" or a "peer"


Orderer

Name: 
The orderer of the network is maintained as a separate organisation.

Domain: 
The domain of the orderer is maintained as reliance-network.com.

Hostname: 
The hostname of the orderer is taken as the functionality itself, 
which in our case is “orderer.”

Utilise the hyperledger/fabric-orderer:latest image to set up the orderer.

Logging level for the orderer from the following subset:
FATAL | PANIC | ERROR | WARNING | INFO | DEBUG

The orderer is TLS enabled.


Peers

Docker Container Name:
The peer for the network is maintained as a unique container.

Domain: 
The domain of the peer is maintained as per the organisation it belongs to: 
<organizational function>.reliance-network.com.

Hostname: 
The hostname for the peer is taken as the index, 
itself which in our case is “peer0” or “peer1.”

Utilise the hyperledger/fabric-peer:latest image to set up the peer.

Logging level for the peer from the following subset: 
FATAL | PANIC | ERROR | WARNING | INFO | DEBUG

The peer is TLS enabled.

The gossip leader election for peers should is kept as true.

The gossip protocol to communicate internally with the peer
adjacent to the peer receiving the message.

The certificate for each peer is generated as per the specification mentioned above.



Setting up Genesis Blocks and Anchor Peers
The following set of rules are followed to set up genesis blocks and anchor peers:

 

Organisational identities

Each organisation is tied to a local MSP.

Each organisation will host an anchor peer. 
 

Capabilities

Any orderer that is running Hyperledger Fabric tools above 1.1 can connect to the network.
Any peer that is running Hyperledger Fabric tools above 1.3 can connect to the network.
Any channel that is running Hyperledger Fabric tools above 1.3 can connect to the network.
Any application that is running Hyperledger Fabric tools above 1.3 can connect to the network.


Consortium

As this solution is used by all the umbrella companies of Reliance, 
that’s why consortium will also be maintained by all the companies under Reliance.

 

Orderer configuration

After putting a lot of thought into how the transactions will be confirmed over the blockchain, 
Reliance came up with expected results from the orderer. The details for the same are as follows:

 
The ordering service is required to run over port 7050.

The Kafka service is required to run over port 9092.

Kafka will be configured on the same localhost as the ordering service.

The block or batch time for the network will be kept at 5 seconds.

A maximum of 10 transactions can be included in the block.

The threshold for the block size is 256 MB, but the preferred size is 512 KB.

Note:

Make sure that the channel and anchor peers follow the same definition as mentioned above.

Also, ensure that you set at least one peer to run the command-line interface for the network.
