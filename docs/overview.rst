
************
Overview
************

.. note:: Please note that these documents are still being drafted and subject to change. 


Whiteblock is a full-stack blockchain testing platform that helps development teams quickly test & deploy high-performing distributed ledger technologies. 

The Whiteblock platform allows users to provision multiple fully-functioning nodes (>1000) within a private test network over which they have complete control. Transactions, behaviors, and other logic can be automated as nodes interact in real-time, allowing testers to observe the performance of protocols, algorithms, decentralized applications, or changes to system infrastructure prior to deployment. 

Each node exists within its own Virtual Local Area Network (VLAN) and is assigned a unique IP address. This provides logical separation between nodes. The links between these nodes can be configured with latency, packet loss, and other WAN conditions according to user specification in order to replicate real-world performance that is accurate within .01 milliseconds.

Use Cases
=========================

  -	Simulate Live, Global Network Performance
  -	Configure Latency, Packet Loss, & Bandwidth.
  - Real-Time Data & Statistics 
  -	Provision & Configure Multiple Independent Nodes
  -	Test Fault Tolerance
  -	Automate Transactions By Size, Frequency, & Rate.
  -	Private, Integrated Development Environment
  - Compile, Deploy, & Functionally Test Smart Contracts

Features
=========================
  -	**Blockchain Agnostic** - Deploy from list of supported clients with appropriate testing libraries or bring your own into the Whiteblock environment. 
  - **Automate Genesis Ceremony** - Quickly provision a functional blockchain network without the additional hassle of editing a configuration file every time a new test network is provisioned.
  - **Account & Wallet Creation** - Indicate total number of accounts/wallets to be created within network. 
  - **Pre-allocate Funds** - Fund wallets and accounts with a specified amount of assets. Start testing right away without the need to wait for mining rewards. 
  - **Transactional Logic** - Indicate the value and volume of transactions to automate activity. Measure transactions per second (TPS) and observe the effects of various environmental conditions on throughput.
  - **Network Behavior** - Configure Wide Area Network (WAN) conditions between nodes, including latency, packet loss, and bandwidth constraints to replicate real-world performance within a safe and controlled environment. 
  - **Data Visualization** - The Whiteblock Explorer provides insight into TPS, uncle rate, and other relevant data points and performance metrics.
  - **Reporting** - Generate concise reports to summarize your test cases. 
  - **Pipeline Integration** - Whiteblock seamlessly integrates with your CI/CD platform of choice to reduce development overhead.
  
Network Specifications
=========================
  - Bandwith Capabilities: Up To 1 00Gb/s 
  - Maximum Nodes: >20,000 
  - Maximum Latency: 20S I 20,000 MS 
  - Packet Loss: Random, Periodic, Burst, BER, Gilbert-Elliot Time Accuracy: Within .01 Milliseconds 

Supported Clients
=========================

While the platform itself is blockchain agnostic, several clients are natively supported. 

Some of these clients include: 

  - Ethereum (Geth & Parity)
  - Bitcoin
  - Syscoin
  - EOS
  - Hyperledger Fabric
  - Hyperledger Sawtooth
  - Quorum
  - NEM 
  - Monero
  
.. note:: Do you have a client of your own that you would like Whiteblock to support?
          Feel free to contact the team via email at `hello@whiteblock.io` or join one of 
          our community channels.



  
  
