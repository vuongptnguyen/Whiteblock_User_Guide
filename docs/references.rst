************
References
************

.. note:: Please note that these documents are still being drafted and subject to change. 
          This page is particularly rough, so take it easy, buddy. 


Command Line Interface
=========================

.. code-block:: console

  whiteblock <command> [FLAGS]

This application will deploy a blockchain, create nodes, and allow those nodes to interact in the network. 

- Available Commands:
    - `build` Build a blockchain using image and deploy nodes
    - `get` Get server and network information.
    - `geth` Run geth commands
    - `help` Displays help page
    - `netconfig` Network conditions
    - `rpc` Rpc interacts with the blockchain
    - `ssh` SSH into an existing container. 
    - `version` Display Whiteblock CLI version

- Flags:
    - -h, --help : help for whiteblock

Fowarding Commands
=========================
- forward
    - forward {"nodes":[<node1>,...<noden>],"port":<port>,"data":"<data to send to all the nodes given>"}
    - forward tcp data to specific nodes, pass data with c string escapes and receive data back with c string escapes, in a json array of strings
    - Example: {"nodes":[1,2],"port":80,"data":"GET / HTTP/1.1\r\n\r\n"}
    - Response: JSON Array of the responses
    - Response Example: ["HTTP/1.1 200 OK\r\n\r\n"]

build
=========================

.. code-block:: console

  whiteblock build [FLAGS]

Aliases: build, create, init

Build will create and deploy a blockchain and the specified number of nodes. Each node will be instantiated in its own container and will interact individually as a participant of the specified network.

- Flags:
    - -h, --help: help for build
    - -a, --server-addr string: server address with port 5000 (default "localhost:5000")

get
=========================

.. code-block:: console

  whiteblock get <command> [FLAGS]

Get will ouput server and network information and statstics.

- Available Commands:
    - data Data will pull data from the network and output into a file.
    - nodes Nodes will show all nodes in the network.
    - server Get server information.
    - stats Get stastics of a blockchain

- Flags:
    - -h, --help : help for get
    - -a, --server-addr string: server address with port 5000 (default "localhost:5000")

**get data**

.. code-block:: console

  whiteblock get data <command> [FLAGS]

Data will pull specific or all block data from the network and output into a file. You will specify the directory where the file will be downloaded.

- Available Commands:
    - all All will pull data from the network and output into a file.
    - block Data block will pull data from the network and output into a file.
    - time Data time will pull data from the network and output into a file.

- Flags:
    - -h, --help : help for data
    - -a, --server-addr string: server address with port 5000 (default "localhost:5000")


**get data all**

.. code-block:: console

  whiteblock get data all [PATH] [FLAGS]

Data all will pull all data from the network and output into a file. The directory where the file will be downloaded will need to be specified. If no directory is provided, default directory is set to ~/Downloads.

Response: JSON representation of network statistics

- Flags:
    - -h, --help : help for all
    - -a, --server-addr string: server address with port 5000 (default "localhost:5000")

**get data block**

.. code-block:: console

  whiteblock get data block <start block> <end block> [PATH] [FLAGS]

Data block will pull block data from the network from a given start and end block and output into a file. The directory where the file will be downloaded will need to be specified. If no directory is provided, default directory is set to ~/Downloads.

Params: Block numbers Format: <start block number> <end block number>

Response: JSON representation of network statistics

- Flags:
    - -h, --help : help for block
    - -a, --server-addr string: server address with port 5000 (default "localhost:5000")

**get data time**

.. code-block:: console

  whiteblock get data time <start time> <end time> [PATH] [FLAGS]

Data time will pull block data from the network from a given start and end time and output into a file. The directory where the file will be downloaded will need to be specified. If no directory is provided, default directory is set to ~/Downloads.

Params: Unix time stamps Format: <start unix time stamp> <end unix time stamp>

Response: JSON representation of network statistics

- Flags:
    - -h, --help : help for time
    - -a, --server-addr string: server address with port 5000 (default "localhost:5000")


**get nodes**

.. code-block:: console

  whiteblock get nodes [FLAGS]

Aliases: nodes, node

Nodes will output all of the nodes in the current network.

- Flags:
    - -h, --help : help for server
    - -a, --server-addr string: server address with port 5000 (default "localhost:5000")

**get server**

.. code-block:: console

  whiteblock get server [FLAGS]

Aliases: server, servers

Server will allow the user to get server information.

- Flags:
    - -h, --help : help for server
    - -a, --server-addr string: server address with port 5000 (default "localhost:5000")


**get stats**

.. code-block:: console

  whiteblock get stats <command> [FLAGS]

Stats will allow the user to get statistics regarding the network.

Response: JSON representation of network statistics

- Available Commands:
    - all
    - block
    - time
- Flags:
    - -h, --help : help for stats
    - -a, --server-addr string: server address with port 5000 (default "localhost:5000")

**get stats all**

.. code-block:: console

  whiteblock get stats all [FLAGS]

Stats all will allow the user to get all the statistics regarding the network.

Response: JSON representation of network statistics

- Flags:
    - -h, --help : help for all
    - -a, --server-addr string: server address with port 5000 (default "localhost:5000")

**get stats block**

.. code-block:: console

  whiteblock get stats block <start block> <end block> [FLAGS]

Stats block will allow the user to get statistics regarding the network.

Params: Block numbers Format: <start block number> <end block number>

Response: JSON representation of network statistics

- Flags:
    - -h, --help : help for block
    - -a, --server-addr string: server address with port 5000 (default "localhost:5000")

**get stats time**

.. code-block:: console

  whiteblock get stats time <start time> <end time> [FLAGS]

Stats time will allow the user to get statistics by specifying a start time and stop time (unix time stamp).

Params: Unix time stamps Format: <start unix time stamp> <end unix time stamp>

Response: JSON representation of network statistics

- Flags:
    - -h, --help : help for time
    - -a, --server-addr string: server address with port 5000 (default "localhost:5000")

netconfig
=========================

.. code-block:: console
  
  whiteblock netconfig <command> [FLAGS]

Netconfig will introduce persistnace network conditions for testing. Use '?' at any time for more help on configuring the network.

Custom Command: netconfig <engine number> <path number> <command>

set delay <amount> Specifies the latency to add [ms]; set loss loss <amount> Specifies the amount of packet loss to add [%]; set bw <amount> <type> Specifies the bandwidth of the network [bps|Kbps|Mbps|Gbps];

- Available Commands:
    - bandwidth Set bandwidth
    - delay Set latency
    - loss Set packetloss
    - off Turn off emulation
    - on Turn on emulation

- Flags:
    -h, --help: help for netconfig

**netconfig bandwidth**

.. code-block:: console

  whiteblock netconfig bandwidth <engine number> <path number> <amount> <bandwidth type> [FLAGS]

Aliases: bw

Bandwidth will constrict the network to the specified bandwidth. You will specify the amount of bandwdth and the type.

Fomat: bandwidth type: bps, Kbps, Mbps, Gbps

- Flags:
    - -h, --help: help for bandwidth

**netconfig delay**

.. code-block:: console
  
  whiteblock netconfig delay <engine number> <path number> <amount> [FLAGS]

Aliases: delay, latancy, lat

Latency will introduce delay to the network. You will specify the amount of latency in ms.

- Flags:
    - -h, --help: help for latency

**netconfig loss**

.. code-block:: console
  
  whiteblock netconfig loss <engine number> <path number> <percent> [FLAGS]

Aliases: packetloss

Packetloss will drop packets in the network. You will specify the amount of packet loss in %.

- Flags:
    - -h, --help: help for loss

**netconfig off**

.. code-block:: console

  whiteblock netconfig off <engine number> [FLAGS]

Turn off emulation.

- Flags:
    - -h, --help: help for off

**netconfig on**

.. code-block:: console
  
  whiteblock netconfig on <engine number> [FLAGS]

Turn on emulation.

- Flags:
    - -h, --help: help for on

SSH 
=============================

.. code-block:: console
  
  whiteblock ssh <server> <node> [FLAGS]

SSH will allow the user to go into the contianer where the specified node exists.

Response: stdout of the command

- Flags:
    - -h, --help : help for ssh
    - -a, --server-addr : server address with port 5000 (default "localhost:5000")

version
=============================

.. code-block:: console

  whiteblock version

Get whiteblock CLI client version

- Flags:
  - -h, --help : help for version

Smart Contracts
=============================

**contractadd**

.. code-block:: console
  
  whiteblock contractadd <filename> [FLAGS]

Adds the specified smart contract into the /Downloads folder.

- Flags:
    - -h, --help: help for contractadd
    - -p, --path string : File path where the smart contract is located

**contractcompile**

.. code-block:: console
  
  whiteblock contractcompile <filename> [FLAGS]

Compiles the specified smart contract.

- Flags:
    - -h, --help: help for contractcompile
    - -p, --path string: File path where the smart contract is located

Ethereum
=============================

- eth::get_block_number
    - Description: Get the current highest block number of the chain
    - Params: None
    - Response: The block number e.g. 10
- eth::get_block
    - Description: Get the data of a block
    - Params: The block number
    - Format: <Block Number>
    - Example: 10
    - Response: JSON Representation of the block. Example
- eth::get_accounts
    - Description: Get the unlocked accounts
    - Params: None
    - Response: A JSON array of the accounts
- eth::get_balance
    - Description: Get the current balance of an account
    - Params: Account address
    - Format: <address>
    - Example: 0xbfa767eae64753e4c426ea42470abf7e4fc305ab
    - Response: The integer balance of the account in wei
- eth::send_transaction
    - Description: Send a transaction between two accounts
    - Params: Sending account, receiving account, gas, gas price, amount to send, transaction data, nonce
    - Format: <from> <to> <gas> <gas price> <value> [data] [nonce]
    - Example: 0xbfa767eae64753e4c426ea42470abf7e4fc305ab 0x8d12a197cb00d4747a1fe03395095ce2a5cc6819 0x015f90 0x165a0bc00 0xde0b6b3a7640000
    - Response: The transaction hash
- eth::get_transaction_count
    - Description: Get the transaction count sent from an address, optionally by block
    - Params: The sender account, a block number
    - Format: <address> [block number]
    - Example: 0xbfa767eae64753e4c426ea42470abf7e4fc305ab
    - Response: The transaction count
- eth::get_transaction
    - Description: Get a transaction by its hash
    - Params: The transaction hash
    - Format: <hash>
    - Example: 0x402c257c85c398154b8b16fa612df13e197135f63d1be9e03b6d2d55285e8670
    - Response: JSON representation of the transaction. Example
- eth::get_transaction_receipt
    - Description: Get the transaction receipt by the tx hash
    - Params: The transaction hash
    - Format: <hash>
    - Example: 0x402c257c85c398154b8b16fa612df13e197135f63d1be9e03b6d2d55285e8670
    - Response: JSON representation of the transaction receipt. Example
- eth::get_hash_rate
    - Description: Get the current hash rate per node
    - Params: None
    - Response: The hash rate of a single node in the network
- eth::start_transactions
    - Description: Start sending transactions according to the given parameters, value = -1 means randomize value.
    - Params: The amount of transactions to send in a second, the value of each transaction in wei, the destination for the transaction
    - Format: <tx/s> <value> [destination]
    - Example: 100 0xde0b6b3a7640000 0x8d12a197cb00d4747a1fe03395095ce2a5cc6819
    - Response: None
- eth::stop_transactions
    - Description: Stops the sending of transactions if transactions are currently being sent
    - Params: None
    - Response: None
- eth::start_mining
    - Description: Send the start mining signal to nodes, may take a while to take effect due to DAG generation
    - Params: A list of the nodes to start mining or None for all nodes
    - Format: [node 1 number] [node 2 number]...
    - Example: 0 1 2 3
    - Response: The number of nodes which successfully received the signal to start mining
- eth::stop_mining
    - Description: Send the stop mining signal to nodes
    - Params: A list of the nodes to stop mining or None for all nodes
    - Format: [node 1 number] [node 2 number]...
    - Example: 0 1 2 3
    - Response: The number of nodes which successfully received the signal to stop mining
- eth::block_listener
    - Description: Get all blocks and continue to subscribe to new blocks
    - Params: The block number to start at or None for all blocks
    - Format: [block number]
    - Example: 12
    - Response: Will emit on eth::block_listener for every block after the given block or 0 that exists/has been created
- eth::get_recent_sent_tx
    - Description: Get a number of the most recent transactions sent
    - Params: The number of transactions to retrieve
    - Format: [number]
    - Example: 5
    - Response: Data on the 5 last sent transactions
    - Response Example: 

    .. code-block:: JSON

      {"results":[{"statement_id":0,"series":[{"name":"transactions","columns":["time","from","gas","gas_price","to","txid","value"],"values":[["2018-11-08T18:02:59.700086831Z","\"0x1949d6d0dfb19048563b602d9a02c06420421429\"","\"0x15f90\"","\"0x3B9ACA00\"","\"0xd9075634d9725f05a1a84343fb40a31d9964ffa5\"","\"0xaffad4a457d79448f211654be8eae1ca6fa8e005936d72528d394fe724adb903\"","0xDE0B6B3A7640000"],["2018-11-08T18:02:59.698273467Z","\"0x1949d6d0dfb19048563b602d9a02c06420421429\"","\"0x15f90\"","\"0x3B9ACA00\"","\"0xd9075634d9725f05a1a84343fb40a31d9964ffa5\"","\"0x8f08bc904c7fbf2e3c695bd71237432137e4f22a20287eda880ed8b409032580\"","0xDE0B6B3A7640000"],["2018-11-08T18:02:59.655393436Z","\"0xd9075634d9725f05a1a84343fb40a31d9964ffa5\"","\"0x15f90\"","\"0x3B9ACA00\"","\"0xe33e509fea81ea03333a3659c98108196ac438a7\"","\"0x21ed0c41959ec9aecf36461cd5b42e65505090e8dbd514ba3b123a3889a5735e\"","0xDE0B6B3A7640000"],["2018-11-08T18:02:59.651551261Z","\"0x1949d6d0dfb19048563b602d9a02c06420421429\"","\"0x15f90\"","\"0x3B9ACA00\"","\"0xd9075634d9725f05a1a84343fb40a31d9964ffa5\"","\"0xfc9b2658bdc95669ffd38e8ff02b9995d894542db52161fbe41ee5dcaed70628\"","0xDE0B6B3A7640000"],["2018-11-08T18:02:59.628233357Z","\"0xd9075634d9725f05a1a84343fb40a31d9964ffa5\"","\"0x15f90\"","\"0x3B9ACA00\"","\"0xe33e509fea81ea03333a3659c98108196ac438a7\"","\"0x15597db936fc88d8a781ea7da6dce1260a05f10070ab75cd8328659d1343390a\"","0xDE0B6B3A7640000"]]}]}]}

**Starting Transactions**

.. code-block:: javascript

  const io = require('socket.io-client')
  const socket = io('http://localhost:5000', {
      path: '/'
  })

  socket.on('connect', () => {
      console.log("Starting the transactions")
      socket.emit("eth::stop_transactions")//kill any previous transaction logic
      socket.emit("eth::start_transactions","1 0xde0b6b3a7640000")//Start sending the transactions
  })

  socket.open();

**Note**: Any configuration option can be left out, and this entire section can even be null, the example contains all of the defaults.

**Ethereum Options**

- chainId: The chain id set in the genesis.conf
- networkId: The network id
- difficulty: The initial difficulty set in the genesis.conf file
- initBalance: The initial balance for the accounts
- maxPeers: The maximum number of peers for each node
- gasLimit: The initial gas limit
- homesteadBlock: Set in genesis.conf
- eip155Block: Set in genesis.conf
- eip158Block: Set in genesis.conf

Example (using defaults)

.. code-block:: javascript

  {
      "chainId":15468,
      "networkId":15468,
      "difficulty":100000,
      "initBalance":100000000000000000000,
      "maxPeers":1000,
      "gasLimit":4000000,
      "homesteadBlock":0,
      "eip155Block":0,
      "eip158Block":0
  }

**geth**

.. code-block:: console

  whiteblock geth <command> [FLAGS]

Geth will allow the user to get infromation and run geth commands.

- Available SubCommands:
    - block_listener Get block listener
    - get_accounts Get account information
    - get_balance Get account balance information
    - get_block Get block information
    - get_block_number Get block number
    - get_hash_rate Get hasg rate
    - get_recent_sent_tx Get recently sent transaction
    - get_transaction Get transaction information
    - get_transaction_count Get transaction count
    - get_transaction_receipt Get transaction receipt
    - send_transaction Sends a transaction
    - start_mining Start Mining
    - start_transactions Start transactions
    - stop_mining Stop mining
    - stop_transactions Stop transactions
- Flags:
    - -h, --help: help for geth
    - -a, --server-addr string: server address with port 5000 (default "localhost:5000")

**geth block_listener**

.. code-block:: console

  whiteblock geth block_listener [block number] [FLAGS]

Get all blocks and continue to subscribe to new blocks

Format: [block number] Params: The block number to start at or None for all blocks Response: Will emit on eth::block_listener for every block after the given block or 0 that exists/has been created

- Flags:
    - -h, --help: help for block_listener

**geth get_accounts**

.. code-block:: console

  whiteblock geth get_accounts [FLAGS]

Get a list of all unlocked accounts

Response: A JSON array of the accounts

- Flags:
    - -h, --help: help for get_accounts

**geth get_balance**

.. code-block:: console

  whiteblock geth get_balance <address> [FLAGS]

Get the current balance of an account

Format: <address> Params: Account address Response: The integer balance of the account in wei

- Flags:
  - -h, --help: help for get_balance

**geth get_block**

.. code-block:: console

  whiteblock geth get_block <block number> [FLAGS]

Get the data of a block

Format: <Block Number> Params: Block number

- Flags:
    - -h, --help: help for get_block

**geth get_block_number**

.. code-block:: console

  whiteblock geth get_block_number [FLAGS]

Get the current highest block number of the chain

Response: The block number

- Flags:
    - -h, --help: help for get_block_number

**geth get_hash_rate**

.. code-block:: console

  whiteblock geth get_hash_rate [FLAGS]

Get the current hash rate per node

Response: The hash rate of a single node in the network

- Flags:
    - -h, --help: help for get_hash_rate

**geth get_recent_sent_tx**

.. code-block:: console

  whiteblock geth get_recent_sent_tx [NUMBER] [FLAGS]

Get a number of the most recent transactions sent

Format: [number] Params: The number of transactions to retrieve Response: JSON object of transaction data

- Flags:
    - -h, --help: help for get_recent_sent_tx

**geth get_transaction**

.. code-block:: console

  whiteblock geth get_transaction <hash> [FLAGS]

Get a transaction by its hash

Format: <hash> Params: The transaction hash

Response: JSON representation of the transaction.

- Flags:
    - -h, --help: help for get_transaction

**geth get_transaction_count**

.. code-block:: console
  
  whiteblock geth get_transaction_count <address> [BLOCK NUMBER] [FLAGS]

Get the transaction count sent from an address, optionally by block

Format: <address> [block number] Params: The sender account, a block number Response: The transaction count

- Flags:
    - -h, --help: help for get_transaction_count

**geth get_transaction_receipt**

.. code-block:: console

  whiteblock geth get_transaction_receipt <hash> [FLAGS]

Get the transaction receipt by the tx hash

Format: <hash> Params: The transaction hash Response: JSON representation of the transaction receipt.

- Flags:
    - -h, --help: help for get_transaction_receipt

**geth send_transaction**

.. code-block:: console
  
  whiteblock geth send_transaction <from address> <to address> <gas> <gas price> <value to send> [FLAGS]

Send a transaction between two accounts

Format: <from> <to> <gas> <gas price> <value> Params: Sending account, receiving account, gas, gas price, amount to send, transaction data, nonce Response: The transaction hash

- Flags:
  - -h, --help: help for send_transaction

**geth start_mining**

.. code-block:: console

  whiteblock geth start_mining [node 1 number] [node 2 number]... [FLAGS]

Send the start mining signal to nodes, may take a while to take effect due to DAG generation

Format: [node 1 number] [node 2 number]... Params: A list of the nodes to start mining or None for all nodes Response: The number of nodes which successfully received the signal to start mining

- Flags:
    - -h, --help: help for start_mining

**geth start_transactions**

.. code-block:: console

  whiteblock geth start_transactions <tx/s> <value> [DESTINATION] [FLAGS]

Start sending transactions according to the given parameters, value = -1 means randomize value.

Format: <tx/s> <value> [destination] Params: The amount of transactions to send in a second, the value of each transaction in wei, the destination for the transaction

- Flags:
    - -h, --help: help for start_transactions
    - geth stop_mining

**geth stop_mining**

.. code-block:: console
  
  whiteblock geth stop_mining [node 1 number] [node 2 number]... [FLAGS]

Send the stop mining signal to nodes

Format: [node 1 number] [node 2 number]... Params: A list of the nodes to stop mining or None for all nodes Response: The number of nodes which successfully received the signal to stop mining

- Flags:
     - -h, --help: help for stop_mining

**geth stop_transactions**

.. code-block:: console
  
  whiteblock geth stop_transactions [FLAGS]

Stops the sending of transactions if transactions are currently being sent

- Flags:
    - -h, --help: help for stop_transactions
    
 **Geth (Go-Ethereum)**

**Note**: Any configuration option can be left out, and this entire section can even be null, the example contains all of the defaults

**Options**

- chainId: The chain id set in the genesis.conf
- networkId: The network id
- difficulty: The initial difficulty set in the genesis.conf file
- initBalance: The initial balance for the accounts
- maxPeers: The maximum number of peers for each node
- gasLimit: The initial gas limit
- homesteadBlock: Set in genesis.conf
- eip155Block: Set in genesis.conf
- eip158Block: Set in genesis.conf

**Example (using defaults)**

.. code-block:: javascript

  {
      "chainId":15468,
      "networkId":15468,
      "difficulty":100000,
      "initBalance":100000000000000000000,
      "maxPeers":1000,
      "gasLimit":4000000,
      "homesteadBlock":0,
      "eip155Block":0,
      "eip158Block":0
  }


Syscoin
=========================
**Syscoin (RegTest)**

Options:

- rpcUser: The username credential
- rpcPass: The password credential
- masterNodeConns: The number of connections to set up for the master nodes
- nodeConns: The number of connections to set up for the normal nodes
- percentMasternodes: The percentage of the network consisting of master nodes
- options: Options to set enabled for all nodes
- senderOptions: Options to set enabled for senders
- receiverOptions: Options to set enabled for receivers
- mnOptions: Options to set enabled for master nodes
- extras: Extra options to add to the config file for all nodes
- senderExtras: Extra options to add to the config file for senders
- receiverExtras: Extra options to add to the config file for receivers
- mnExtras: Extra options to add to the config file for master nodes

- sys::start_test
    - Description: Start the propogation/tps test for syscoin
    - Params: The max number of test results to retrieve
    - Format: {"waitTime":<seconds to wait>,"minCompletePercent":<percentage>,"numberOfTransactions":<number of tx>}
    - Example:

    .. code-block:: JSON

      {
          "waitTime":11,
          "minCompletePercent":97.7,
          "numberOfTransactions":500
      }

- sys::get_recent_test_results
    - Description: Get recent test results
    - Params: The max number of test results to retrieve
    - Format: [number]
    - Example: 5
    - Response: Data on the last x test results


.. code-block:: console
  
  whiteblock sys <command> [FLAGS]

Alias: SYS, syscoin

Sys will allow the user to get infromation and run SYS commands.

- Available Commands:
    - test SYS test commands.

- Flags:
    - -h, --help : help for sys

**sys test**

.. code-block:: console

  whiteblock sys test <command> [FLAGS]

Available Commands: results Get results from a previous test. start Starts propagation test.

- Flags:
    - -h, --help : help for test

**sys test start**

.. code-block:: console

  whiteblock sys test start <wait time> <min complete percent> <number of tx> [FLAGS]

Sys test start will start the propagation test. It will wait for the signal start time, have nodes send messages at the same time, and require to wait a minimum amount of time then check receivers with a completion rate of minimum completion percentage.

Format: <wait time> <min complete percent> <number of tx> Params: Time in seconds, percentage, number of transactions

- Flags:
    - -h, --help : help for start
    - -a, --server-addr string: server address with port 5000 (default "localhost:5000")

**sys test results**

.. code-block:: console

  whiteblock sys test results <test number> [FLAGS]

Sys test results pulls data from a previous test or tests and outputs as csv.

Format: <test number> Params: Test number

- Flags:
    - -h, --help : help for results
    - -a, --server-addr string: server address with port 5000 (default "localhost:5000")


**Example (using defaults)**

.. code-block:: JSON

  {
      "rpcUser":"username",
      "rpcPass":"password",
      "masterNodeConns":25,
      "nodeConns":8,
      "percentMasternodes":90,
      "options":[
          "server",
          "regtest",
          "listen",
          "rest"
      ],
      "senderOptions":[
          "tpstest",
          "addressindex"
      ],
      "mnOptions":[],
      "receiverOptions":[
         "tpstest"
      ],
      "extras":[],
      "senderExtras":[],
      "receiverExtras":[],
      "mnExtras":[]
  }

