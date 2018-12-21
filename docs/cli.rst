
************
Command Line Interface
************

.. code-block:: console

  $ whiteblock <command> [FLAGS]

This application will deploy a blockchain, create nodes, and allow those nodes to interact in the network.

Available Commands
=========================

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


Build
=========================

.. code-block:: console

  whiteblock build [FLAGS]

Aliases: build, create, init

Build will create and deploy a blockchain and the specified number of nodes. Each node will be instantiated in its own container and will interact individually as a participant of the specified network.

- Flags:
    - -h, --help: help for build
    - -a, --server-addr string: server address with port 5000 (default "localhost:5000")

Ethereum
-------------------------
Build
+++++++++++++

Mining
+++++++++++++

Automate Transactions
+++++++++++++

Geth commands
+++++++++++++


Rchain
-------------------------
Build
+++++++++++++

Syscoin
-------------------------
Build
+++++++++++++

  
Data Retrieval
=========================
Ethereum
-------------------------
Geth Commands
+++++++++++++

Rchain
-------------------------


Syscoin
-------------------------
sys Commands
+++++++++++++


Get Commands
=========================


  
Netconfig
=========================  
  
SSH
=========================

Version
=========================  
  
  
