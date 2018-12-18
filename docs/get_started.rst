************
Get Started
************

Accessing Whiteblock
=========================
There are two components of the Whiteblock platform:

Graphical User Interface (GUI) - The GUI acts as a data visualization dashboard which provides insight into relevant performance metrics for the blockchain network. 

Command Line Interface (CLI) - Using the CLI application, users can interface with the Whiteblock platform. It provides functionality which allows users to configure the blockchain network, provision nodes, and automate various behaviors and actions within the blockchain network. The following documentation focuses primarily on the CLI application. 


Build The Network
=========================
In this step, we create and deploy a selected blockchain network with the specified client and number of nodes. The Whiteblock platform provisions each node as an independent participant within the blockchain network. Nodes are logically separated from one another within their own Local Area Network (LAN). 

After running the build command as shown below, you will be prompted to customize the blockchain network, this includes configuring the Wide Area Network (WAN) links between each node with latency, packet loss, bandwidth constraints, and other common network characteristics. If this is your first time using the Whiteblock platform, it may be easier to stick with the default parameters provided for each option.  

Command: 

.. code-block:: console

  $ whiteblock build 

Output: 

.. code-block:: console

  blockchain (default set to: ethereum):
  nodes (default set to: 10):
  image (default set to: ethereum:latest):
  cpus (default set to: no limit):
  memory (default set to: no limit):
  Use default parameters? (y/n) y
  2018/12/13 20:07:50 build:  Build in Progress
  Building: 100.000000
  Done







Configure Network Conditions
=============================
To add network latency between nodes, use the following commands: 

.. code-block:: console

  $ whiteblock netconfig delay 1 1 200


The above commands configure the amount of latency between nodes and follows this format: delay <engine number> <path number> <amount>.

The first `1` value refers to emulation engine 1, the second 1 refers to VLAN path 1. The `200` valuerefers to the total amount of one-way latency, which translates to milliseconds. 

  $ whiteblock netconfig on 1


This command turns the netconfig engine on and implements latency on  on engine 1. 

To turn disbale netconfig, use the following command: 

.. code-block:: console

  $ whiteblock netconfig off 1


For more advanced netconfig parameters, please visit the Command Line Reference page. 





Automate Transactions
=========================
After configuring network conditions, transactional logic can be defined and automated for such purposes as throughput tests. Transaction commands adhere to the following format: whiteblock <blockchain-interface> send_transactions <tx/s> <value>. The <blockchain-interface> needs to be consistent with the relevant command used by the client that was indicated when the network was built. 

The transaction engine will automate transactions according to the specified submission rate in the second argument <tx/s> and the amount of assets sent in the third parameter <value>, which is specified in hex. This will immediately begin transactions once the network is finished building, but these values can also be configured and altered once the network has already been built. 

To start transactions, run the following command: 

.. code-block:: console

  $ whiteblock geth start_transactions 100 0x545454
  started


To stop the transaction, run the following command

.. code-block:: console

  $ whiteblock geth stop_transactions
  success


Note: currently we only support geth for sending transaction through command line. To send transaction for other type of blockchains, you can use Websocket API calls. Please refer to the Generics section in the  Websocket API in :doc:`/references` for more information. 


Examine Data
=========================
You may now go to the GUI and use our data visualization tools to examine the different data points that are being push directly from the blockchain.

If you want to quickly check the stats of your current blockchain network, use the following command. 

Command: 

.. code-block:: console

  $ whiteblock get stats all


Output: 

.. code-block:: JSON

  {
    "blockTime": {
      "max": 70,
      "mean": 1.2978947368421072,
      "standardDeviation": 1.7608896643379766
    },
    "difficulty": {
      "max": 329333,
      "mean": 214993.2977380325,
      "standardDeviation": 56914.20143516361
    },
    "gasLimit": {
      "max": 8000000,
      "mean": 7168060.679642294,
      "standardDeviation": 1286432.4077131029
    },
    "gasUsed": {
      "max": 7917000,
      "mean": 534323.5139400318,
      "standardDeviation": 1538475.9696957779
    },
    "totalDifficulty": {
      "max": 408802259,
      "mean": 173546242.58337703,
      "standardDeviation": 117177703.83311588
    },
    "tps": {
      "max": 377,
      "mean": 18.855407894736842,
      "standardDeviation": 58.25808243503218
    },
    "transactionCount": {
      "max": 377,
      "mean": 25.443976854287218,
      "standardDeviation": 73.26076046170377
    },
    "uncleCount": {
      "max": 1,
      "mean": 0.11204629142556508,
      "standardDeviation": 0.3154233979959995
    }
  }


To learn more about how to use our command line features, please visit the :doc:`/references` page. 
