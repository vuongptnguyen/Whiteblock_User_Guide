************
Get Started
************


Build The Network
=========================
In this step, we create and deploy a selected blockchain network with  the specified number of nodes. Each node will be instantiated and will interact individually as a participant of the blockchain network. After we run the build command as shown below, you will be prompted to customized your blockchain. For simplicity, just use the default parameters for all the options.  

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
To add network latency between nodes, you can use the following commands: 

.. code-block:: console

  $ whiteblock netconfig delay 1 1 200
  $ whiteblock netconfig on 1


The first command above use the delay condition for network emulation. The command follow this format: delay <engine number> <path number> <amount>.

The first 1 refers to the emulation engine1, the second 1 refers to the VLAN path1. The 200 here refers to the one-way latency of 200ms. The second command above turn on the netconfig on engine1. 



To turn the netconfig off, you can write: 

.. code-block:: console

  $ whiteblock netconfig off 1


To learn the format of how to use other netconfig parameters, please visit the Command Line Reference page. 





Send Transactions
=========================
After configured the network condition, we want to run some transactions for throughput test. The transaction commands need to follow this format: whiteblock <blockchain-interface> send_transactions <tx/s> <value>. The <blockchain-interface> needs to be consistent with the blockchain type specified in the network building step. This will send transactions with the submission rate specified in the second argument <tx/s> and the amount of assets to send in the third parameter <value>, specified in hex. This will immediately begin transactions has the network been built properly. 

To start the transaction, run the following command: 

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
