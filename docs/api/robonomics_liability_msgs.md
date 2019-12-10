Robonomics Liability Messages
=============================

### robonomics_liability/Liability.msg

| Field         | Type                      | Description                                       |
|-------------- |-------------------------  |------------------------------------------------   |
| address       | ethereum_common/Address   | The Liability’s address                           |
| model         | ipfs_common/Multihash     | CPS behavioral model Identifier                   |
| objective     | ipfs_common/Multihash     | CPS behavioral model parameters in rosbag file    |
| result        | ipfs_common/Multihash     | Liability result hash                             |
| promisee      | ethereum_common/Address   | The promisee address                              |
| promisor      | ethereum_common/Address   | The promisor address (usually CPS)                |
| lighthouse    | ethereum_common/Address   | The address of lighthouse your CPS works on       |
| token         | ethereum_common/Address   | Operational token address                         |
| cost          | ethereum_common/UInt256   | CPS behavioral model implementation cost          |
| validator     | ethereum_common/Address   | Observing network address                         |
| validatorFee  | ethereum_common/UInt256   | Observing network commission                      |

<!--
============== ============================================================ ==================================================
 Field                 Type                                                 Description
============== ============================================================ ==================================================
address        :ref:`ethereum_common/Address <Ethereum-common-Address.msg>` The Liability's address
model          :ref:`ipfs_common/Multihash <IPFS-Common-Multihash.msg>`     CPS behavioral model Identifier
objective      :ref:`ipfs_common/Multihash <IPFS-Common-Multihash.msg>`     CPS behavioral model parameters in rosbag file
result         :ref:`ipfs_common/Multihash <IPFS-Common-Multihash.msg>`     Liability result hash
promisee       :ref:`ethereum_common/Address <Ethereum-common-Address.msg>` The promisee address
promisor       :ref:`ethereum_common/Address <Ethereum-common-Address.msg>` The promisor address (usually CPS)
lighthouse     :ref:`ethereum_common/Address <Ethereum-common-Address.msg>` The address of lighthouse your CPS works on
token          :ref:`ethereum_common/Address <Ethereum-common-Address.msg>` Operational token address
cost           :ref:`ethereum_common/UInt256 <Ethereum-common-UInt256.msg>` CPS behavioral model implementation cost
validator      :ref:`ethereum_common/Address <Ethereum-common-Address.msg>` Observing network address
validatorFee   :ref:`ethereum_common/UInt256 <Ethereum-common-UInt256.msg>` Observing network commission
============== ============================================================ ==================================================
-->

### robonomics_liability/StartLiability.srv

**Request**

| Field     | Type              | Description                                           |
|---------  |-----------------  |-----------------------------------------------------  |
| address   | std_msgs/String   | The address of Liability you are willing to execute   |

**Response**

| Field     | Type              | Description                               |
|---------  |-----------------  |------------------------------------------ |
| success   | std_msgs/Bool     | Weather or not the Liability was started  |
| msg       | std_msgs/String   | Status of launch                          |

### robonomics_liability/FinishLiability.srv

**Request**

| Field     | Type              | Description                           |
|---------  |-----------------  |------------------------------------   |
| address   | std_msgs/String   | The address of Liability to finish    |
| success   | std_msgs/Bool     | The status of execution               |

**Response**

The response is empty

