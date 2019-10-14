Project Structure 

The folder bin will have the Hyperledger binaries used to build the network configuration. 

 
The network folder will contain the following sub-folders: 

1. channel-artifacts: 

This folder contains the channel-artifacts required to bootstrap the blockchain network.
Essentially this folder contains the following files:

genesis.block
channel.tx
anchor.tx files for each organisation

2. crypto-config: 
This folder contains the cryptographic materials required for identifying the
various participants of the fabric-network. 

Apart from these two folders, the network folder also have the following configuration files: 

a. configtx.yaml- 
The configuration file used to define the properties of organisations 
that will be the part of the fabric-network.

b. crypto-config.yaml- 
The configuration file used by the 'cryptogen' tool to generate 
cryptographic materials for the network. 

c. docker-compose.yaml- The configuration file used by 

 

The Composer folder contains the smart contract of the Asset Tracking System 
built using Hyperledger Composer. This folder contains the following components:

model.cto: 
This file holds the definitions of all the resources 
(assets, participants and transactions in the network).

permissions.acl: 
This file holds all the rules that govern the network.

script.js: 
This file holds all the business logic. 