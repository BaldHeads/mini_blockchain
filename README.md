# mini_blockchain
a testnet blockchain using Puppeth, Geth, &amp; the Clique Proof of Authority algorithm

---
## Setup
links:
- Download & install the MyCrypto Desktop App for your OS at https://download.mycrypto.com/
- Download the most recent **GETH & TOOLS** for your OS and version (32 or 64 bit )at https://geth.ethereum.org/downloads/
    - extract the contents to a location easy to reach and rename the folder blockchain-tools or something similar
---
## Code Guide for blockchain setup
1. Create Accounts/Nodes
    - `./geth --datadir poa_node1 account new` 
    - `./geth --datadir poa_node2 account new `
    - "use geth to create a data directory for each node's new account information"

2. Block Genesis (press enter after completing each step)
    - `./puppeth` 
        - name your network (mine is toutengnet)
        - configure new genesis from scratch: option 2;1
        - choose consensus algorithm (clique- PoA)
        - paste addresses to be prefunded without the first 0x 
        - choose **NO** for prefund with 1 wei
        - input & **REMEMBER** a chain ID (mine is 123)
        - when genesis is completed, `manage existing genesis` and then `export genesis configurations`


3. Initialize & Mine (the two lines of command line code will be run in separate windows; one for node1 & one for node2)
    - Init
        - `./geth --datadir poa_node1 init toutengnet.json`
        - `./geth --datadir poa_node2 init toutengnet.json`
    - Mine
        - `./geth --datadir poa_node1 --unlock "poa_node1_address" --mine --rpc --allow-insecure-unlock`
            - **IMMEDIATELY** copy the self-enode from the first node to paste into the long portion starting with "enode" below


        - `./geth --datadir poa_node2 --unlock "poa_node2_address" --mine --port 30304 --bootnodes "poa_node1_enode_address@127.0.0.1:30303" --ipcdisable --allow-insecure-unlock`

At this point, both nodes should be running 

---
## MyCrypto Setup and Transaction Generation

- In the MyCrypto app, change network to "Add Custom Node" then create the node using information setup from the block genesis. 
- The network should be set to custom, currency to ETH, and chainID is the same from the genesis. 
    - Note the URL is the same as the sample just **http://** instead of https://.
    ![]()

