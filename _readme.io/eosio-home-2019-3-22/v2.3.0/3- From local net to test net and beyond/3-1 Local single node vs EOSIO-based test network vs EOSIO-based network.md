---
title: "3.1 Local single node vs EOSIO-based test network vs EOSIO-based network"
excerpt: ""
---
***In this tutorial you will make the transition from the local single node to a test network that is bound to a system contract, at the end of this tutorial you will know what are the differences between these two scenarios with respect to developing a smart contract, deploying it, and testing it.  This will get you very close to learning how to write, deploy, and test on the public EOS network as well as any EOSIO-based networks (either public, private, or test). Also you will learn about the resources a developer has to know about while developing a smart contract.***
[block:api-header]
{
  "title": "3.1.1 Local single node vs EOSIO-based network"
}
[/block]
A local single node is when you launch one nodeos instance and it is the only node that is producing blocks and the only node you interact with. It is the same environment which this journey helped you set up so far, starting with the [Introductory journey](https://developers.eos.io/eosio-home/docs/introduction), continuing with the [Hello world contract](https://developers.eos.io/eosio-home/docs/your-first-contract), [Data persistence in a smart contract](https://developers.eos.io/eosio-home/docs/data-persistence), and finishing with [Contract actions dispatcher](https://developers.eos.io/eosio-home/docs/writing-a-custom-dispatcher), that is, you had only one node running and interacting with.

An EOSIO-based network is any network that is using the EOSIO platform or a fork of EOSIO platform code to launch and run a blockchain. The network, thus the blockchain produced, can be public or can be private as well. Also a network, thus the blockchain produced, can be as well a test network. A test network is exactly that, a EOSIO-based network that is used as a testing environment, its purpose serves for testing the alpha and beta version of new releases of the EOSIO code, or forks of the EOSIO code, and/or smart contracts serving blockchain applications. There can be multiple test networks for the same EOSIO-based network. For example at the time of writing this tutorial, approximately Feb 2019, there are two test networks for the public EOS network (which is e EOSIO-based network), and they are the [Jungle TestNet](https://jungletestnet.io/) and [CryptoKylin TestNet](https://www.cryptokylin.io/).

Throughout this tutorial we will be referencing both mentioned test networks and you will have the option to use any of the two.
[block:api-header]
{
  "title": "3.1.2 Principles governing a EOSIO-based network"
}
[/block]
The next step is to understand a few principles that govern a EOSIO-based network, (either test network, or public or private network).

In a EOSIO-based network the blockchain is kept alive by nodes which are interconnected into a mesh, communicating with each other via peer to peer protocols. Some of these blocks are elected by the token holders to be producer nodes. They produce blocks, validate them and reach consensus on what transactions are allowed in each block, their order, and what blocks are finalized and stored forever in the blockchain memory.

Another aspect, you have to be aware of, is that on local single node the only producing node was governed by the eosio privileged account and because you controlled the eosio public and private keys, practically you did not have limits on the blockchain, because been privileged the eosio account had no restrictions when it comes to resources: RAM, bandwidth or CPU. This tutorial will explain later in details the resources that you have to know about when writing smart contracts on EOSIO-based platforms. On a EOSIO-based test network or on any EOSIO-based network (either public or private) the eosio account is resigned, and the control of the blockchain is in the hands of the nodes which are elected as block producers, and because of this, one consequence is that your smart contract, deployed to the account which you control, via its private and public keys, is limited by the amount of resources your account staked for the contract to use.

    Governance, the mechanism by which collective decisions are made, of the blockchain is achieved through the 21 active block producers which are appointed by token holders' votes. It's the 21 active block producers which continuously create the blockchain by creating blocks, and securing them by validating them, and reaching consensus. Consensus is reached when 2/3+1 active block producers agree on validity of a block, therefore on all transactions contained in it and their order. This aspect was not present on the local test network either.

    To run a smart contract, on the blockchain, the contract has to be deployed to the blockchain using one of the blockchain nodes, in the same manner it was deployed in the previous tutorial on a single node. Only that this time, the node you will deploy to will make sure to transfer it to its peers nodes, and those nodes to its peers and so on and so forth until the transaction that deploys the contract is validated by the minimum number of nodes and thus reaching finality. Once the deploying transaction reaches finality it is stored in the blockchain memory for good. After this, of course, you can alter the contract through other transactions, either modify its code, or deleting the contract altogether. One thing to understand here is that it is the transactions that reached finality the ones that will stay in the blockchain history forever, not the contract code itself, the contract code can be changed by the owner of the contract.

    There are several public, private and test EOSIO-based networks. At the time of the writing of this tutorial, here's a list of them, in no particular order, which is not mentioning probably all of them:
    Public EOSIO-based networks: EOS, Tellos, BOSCORE, Meet.One, Enumivo, EOSForce, UOS.
    Private EOSIO-based networks: Everypedia, WAX, Worbli, EvaCoop.
    Public test EOSIO-based networks: [Jungle TestNet](https://jungletestnet.io/) and [CryptoKylin TestNet](https://www.cryptokylin.io/).