Robonomics Liability Messages
=============================

### robonomics_liability/Liability.msg

| Field         | Type                      | Description                                       |
|-------------- |-------------------------  |------------------------------------------------   |
| address       | [ethereum_commom/Address](ethereum_common_msgs.md#ethereum_commonaddressmsg)   | The Liability’s address                           |
| model         | [ipfs_commom/Multihash](ipfs_common_msgs.md#ipfs_commonmultihashmsg)     | CPS behavioral model Identifier                   |
| objective     | [ipfs_commom/Multihash](ipfs_common_msgs.md#ipfs_commonmultihashmsg)     | CPS behavioral model parameters in rosbag file    |
| result        | [ipfs_commom/Multihash](ipfs_common_msgs.md#ipfs_commonmultihashmsg)     | Liability result hash                             |
| promisee      | [ethereum_commom/Address](ethereum_common_msgs.md#ethereum_commonaddressmsg)   | The promisee address                              |
| promisor      | [ethereum_commom/Address](ethereum_common_msgs.md#ethereum_commonaddressmsg)   | The promisor address (usually CPS)                |
| lighthouse    | [ethereum_commom/Address](ethereum_common_msgs.md#ethereum_commonaddressmsg)   | The address of lighthouse your CPS works on       |
| token         | [ethereum_commom/Address](ethereum_common_msgs.md#ethereum_commonaddressmsg)   | Operational token address                         |
| cost          | [ethereum_commom/UInt256](ethereum_common_msgs.md#ethereum_commonuint256msg)   | CPS behavioral model implementation cost          |
| validator     | [ethereum_commom/Address](ethereum_common_msgs.md#ethereum_commonaddressmsg)   | Observing network address                         |
| validatorFee  | [ethereum_commom/UInt256](ethereum_common_msgs.md#ethereum_commonuint256msg)   | Observing network commission                      |

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

