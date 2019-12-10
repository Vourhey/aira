Market Messages
===============

Market messages is used for exchange **Demand** and **Offer** information. It also used for delivery **Result** messages with liability execution reports.

!!! note
    This is spec for Robonomics `Generation 5`.

* Currently for message delivery is used [IPFS PubSub](https://ipfs.io/blog/25-pubsub/) broadcaster.
* IPFS PubSub **topic** is set according to *Lighthouse* [ENS](https://ens.domains/) name.

Messages content
----------------

Robonomics market message use [JSON](https://www.json.org/) data format.

**Demand**

| Field         | ROS Type                  | Description                                       |
|-------------- |-------------------------  |------------------------------------------------   |
| model         | ipfs_common/Multihash     | CPS behavioral model identifier                   |
| objective     | ipfs_common/Multihash     | CPS behavioral model parameters in rosbag file    |
| token         | ethereum_common/Address   | Operational token address                         |
| cost          | ethereum_common/UInt256   | CPS behavioral model execution cost               |
| lighthouse    | ethereum_common/Address   | Lighthouse contract address                       |
| validator     | ethereum_common/Address   | Observing network address                         |
| validatorFee  | ethereum_common/UInt256   | Observing network fee                             |
| deadline      | ethereum_common/UInt256   | Deadline block number                             |
| nonce         | ethereum_common/UInt256   | Robonomics message counter                        |
| sender        | ethereum_common/Address   | Message sender address                            |
| signature     | std_msgs/UInt8[]          | Sender’s Ethereum signature                       |

<!--
 ============== ============================================================== ================================================
      Field                              ROS Type                                                Description
 ============== ============================================================== ================================================
  model          :ref:`ipfs_common/Multihash <IPFS-Common-Multihash.msg>`       CPS behavioral model identifier
  objective      :ref:`ipfs_common/Multihash <IPFS-Common-Multihash.msg>`       CPS behavioral model parameters in rosbag file
  token          :ref:`ethereum_common/Address <Ethereum-common-Address.msg>`   Operational token address
  cost           :ref:`ethereum_common/UInt256 <Ethereum-common-UInt256.msg>`   CPS behavioral model execution cost
  lighthouse     :ref:`ethereum_common/Address <Ethereum-common-Address.msg>`   Lighthouse contract address
  validator      :ref:`ethereum_common/Address <Ethereum-common-Address.msg>`   Observing network address
  validatorFee   :ref:`ethereum_common/UInt256 <Ethereum-common-UInt256.msg>`   Observing network fee 
  deadline       :ref:`ethereum_common/UInt256 <Ethereum-common-UInt256.msg>`   Deadline block number
  nonce          :ref:`ethereum_common/UInt256 <Ethereum-common-UInt256.msg>`   Robonomics message counter
  sender         :ref:`ethereum_common/Address <Ethereum-common-Address.msg>`   Message sender address
  signature      std_msgs/UInt8[]                                               Sender's Ethereum signature
 ============== ============================================================== ================================================
-->

**Offer**

| Field             | ROS Type                  | Description                                       |
|---------------    |-------------------------  |------------------------------------------------   |
| model             | ipfs_common/Multihash     | CPS behavioral model identifier                   |
| objective         | ipfs_common/Multihash     | CPS behavioral model parameters in rosbag file    |
| token             | ethereum_common/Address   | Operational token address                         |
| cost              | ethereum_common/UInt256   | CPS behavioral model execution cost               |
| validator         | ethereum_common/Address   | Observing network address                         |
| lighthouse        | ethereum_common/Address   | Lighthouse contract address                       |
| lighthouseFee     | ethereum_common/UInt256   | Liability creation fee                            |
| deadline          | ethereum_common/UInt256   | Deadline block number                             |
| nonce             | ethereum_common/UInt256   | Robonomics message counter                        |
| sender            | ethereum_common/Address   | Message sender address                            |
| signature         | std_msgs/UInt8[]          | Sender’s Ethereum signature                       |

<!--
 =============== ============================================================== ================================================
      Field                              ROS Type                                                Description
 =============== ============================================================== ================================================
  model           :ref:`ipfs_common/Multihash <IPFS-Common-Multihash.msg>`       CPS behavioral model identifier
  objective       :ref:`ipfs_common/Multihash <IPFS-Common-Multihash.msg>`       CPS behavioral model parameters in rosbag file
  token           :ref:`ethereum_common/Address <Ethereum-common-Address.msg>`   Operational token address
  cost            :ref:`ethereum_common/UInt256 <Ethereum-common-UInt256.msg>`   CPS behavioral model execution cost
  validator       :ref:`ethereum_common/Address <Ethereum-common-Address.msg>`   Observing network address
  lighthouse      :ref:`ethereum_common/Address <Ethereum-common-Address.msg>`   Lighthouse contract address
  lighthouseFee   :ref:`ethereum_common/UInt256 <Ethereum-common-UInt256.msg>`   Liability creation fee 
  deadline        :ref:`ethereum_common/UInt256 <Ethereum-common-UInt256.msg>`   Deadline block number
  nonce           :ref:`ethereum_common/UInt256 <Ethereum-common-UInt256.msg>`   Robonomics message counter
  sender          :ref:`ethereum_common/Address <Ethereum-common-Address.msg>`   Message sender address
  signature       std_msgs/UInt8[]                                               Sender's Ethereum signature
 =============== ============================================================== ================================================
-->

**Result**

| Field         | ROS Type                  | Description                       |
|-----------    |-------------------------  |---------------------------------- |
| liability     | ethereum_common/Address   | Liability contract address        |
| result        | ipfs_common/Multihash     | Liability result multihash        |
| success       | std_msgs/Bool             | Is liability executed successful  |
| signature     | std_msgs/UInt8[]          | Sender’s Ethereum signature       |

<!--
 =========== ============================================================== ===========================================
    Field                                 ROS Type                                             Description
 =========== ============================================================== ===========================================
  liability   :ref:`ethereum_common/Address <Ethereum-common-Address.msg>`   Liability contract address
  result      :ref:`ipfs_common/Multihash <IPFS-Common-Multihash.msg>`       Liability result multihash
  success     std_msgs/Bool                                                  Is liability executed successful
  signature   std_msgs/UInt8[]                                               Sender's Ethereum signature
 =========== ============================================================== ===========================================
-->

Messages signing
----------------

Before signing the messages is packed using [abi.encodePacked](https://solidity.readthedocs.io/en/latest/abi-spec.html#non-standard-packed-mode
) solidity finction and hashed by Keccak_256.

```solidity

   demandHash = keccak256(abi.encodePacked(
        _model
      , _objective
      , _token
      , _cost
      , _lighthouse
      , _validator
      , _validator_fee
      , _deadline
      , IFactory(factory).nonceOf(_sender)
      , _sender
      ));
```

!!! note
    `nonce` parameter is counted by factory smart contract and incremented for each created liability smart contract.

Message hash are signed using Ethereum ``secp256k1`` [signature](https://github.com/ethereum/wiki/wiki/JSON-RPC#eth_sign).

