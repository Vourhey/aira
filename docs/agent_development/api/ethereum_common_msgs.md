Ethereum Common Messages
========================

## ethereum_common/Address.msg

| Field   	| Type            	| Description                    	|
|---------	|-----------------	|--------------------------------	|
| address 	| std_msgs/String 	| Address in Ethereum blockchain 	|

## ethereum_common/UInt256.msg

| Field   	| Type            	| Description                	|
|---------	|-----------------	|----------------------------	|
| uint256 	| std_msgs/String 	| A wrapper for big integers 	|

## ethereum_common/TransferEvent.msg

| Field      	| Type                                                  	| Description      	|
|------------	|-------------------------------------------------------	|------------------	|
| args_from  	| [ethereum_common/Address](#ethereum_commonaddressmsg) 	| Sender address   	|
| args_to    	| [ethereum_common/Address](#ethereum_commonaddressmsg) 	| Receiver address 	|
| args_value 	| [ethereum_common/UInt256](#ethereum_commonuint256msg) 	| Amount of tokens 	|

## ethereum_common/ApprovalEvent.msg

| Field        	| Type                                                  	| Description      	|
|--------------	|-------------------------------------------------------	|------------------	|
| args_owner   	| [ethereum_common/Address](#ethereum_commonaddressmsg) 	| Owner address    	|
| args_spender 	| [ethereum_common/Address](#ethereum_commonaddressmsg) 	| Spender address  	|
| args_value   	| [ethereum_common/UInt256](#ethereum_commonuint256msg) 	| Amount of tokens 	|

## ethereum_common/AccountBalance.srv

**Request**

| Field   	| Type                                                  	| Description      	|
|---------	|-------------------------------------------------------	|------------------	|
| account 	| [ethereum_common/Address](#ethereum_commonaddressmsg) 	| Ethereum address 	|

**Response**

| Field   	| Type                                                  	| Description    	|
|---------	|-------------------------------------------------------	|----------------	|
| balance 	| [ethereum_common/UInt256](#ethereum_commonuint256msg) 	| Balance in Wei 	|

## ethereum_common/AccountToAddressAllowance.srv

**Request**

| Field   	| Type                                                  	| Description      	|
|---------	|-------------------------------------------------------	|------------------	|
| account 	| [ethereum_common/Address](#ethereum_commonaddressmsg) 	| Ethereum address 	|
| to      	| [ethereum_common/Address](#ethereum_commonaddressmsg) 	| Ethereum address 	|

**Response**

| Field  	| Type                                                  	| Description   	|
|--------	|-------------------------------------------------------	|---------------	|
| amount 	| [ethereum_common/UInt256](#ethereum_commonuint256msg) 	| Balance in Wn 	|

## ethereum_common/Accounts.srv

**Request**

Request is empty

**Response**

=========== ============================================================== =============================================
Field       Type                                                            Description
=========== ============================================================== =============================================
accounts    :ref:`ethereum_common/Address[] <Ethereum-common-Address.msg>`  List of available accounts
=========== ============================================================== =============================================

## ethereum_common/Allowance.srv

**Request**

Request is empty

**Response**

=========== ============================================================ ===============================================
Field       Type                                                          Description
=========== ============================================================ ===============================================
amount      :ref:`ethereum_common/UInt256 <Ethereum-common-UInt256.msg>`  Amount of XRT the Factory is allowed to spend
=========== ============================================================ ===============================================

## ethereum_common/Approve.srv

**Request**

=========== ============================================================ ===============================================
Field       Type                                                          Description
=========== ============================================================ ===============================================
spender     :ref:`ethereum_common/Address <Ethereum-common-Address.msg>`  Who is allowed to spend
value       :ref:`ethereum_common/UInt256 <Ethereum-common-UInt256.msg>`  How much tokens are allowed
=========== ============================================================ ===============================================

**Response**

=========== ============================================================ ===============================================
Field       Type                                                            Description
=========== ============================================================ ===============================================
txhash      std_msgs/Uint8[32]                                              Transaction hash
=========== ============================================================ ===============================================

## ethereum_common/Balance.srv

**Request**

Request is empty

**Response**

=========== ============================================================ ===============================================
Field       Type                                                          Description
=========== ============================================================ ===============================================
balance     :ref:`ethereum_common/UInt256 <Ethereum-common-UInt256.msg>`  The balance of default account
=========== ============================================================ ===============================================

## ethereum_common/BlockNumber.srv

**Request**

Request is empty

**Response**

=========== ============================================================ ===============================================
Field       Type                                                            Description
=========== ============================================================ ===============================================
number      std_msgs/Uint64                                                 Current block number
=========== ============================================================ ===============================================

## ethereum_common/Transfer.srv

**Request**

=========== ============================================================ ===============================================
Field       Type                                                           Description
=========== ============================================================ ===============================================
to          :ref:`ethereum_common/Address <Ethereum-common-Address.msg>`   Ethereum address
value       :ref:`ethereum_common/UInt256 <Ethereum-common-UInt256.msg>`   The amount of tokens
=========== ============================================================ ===============================================

**Response**

=========== ============================================================ ===============================================
Field       Type                                                            Description
=========== ============================================================ ===============================================
txhash      std_msgs/Uint8[32]                                              Transaction hash
=========== ============================================================ ===============================================

## ethereum_common/TransferFrom.srv

**Request**

=========== ============================================================ ===============================================
Field       Type                                                           Description
=========== ============================================================ ===============================================
owner       :ref:`ethereum_common/Address <Ethereum-common-Address.msg>`   Owner's address
to          :ref:`ethereum_common/Address <Ethereum-common-Address.msg>`   Another account
value       :ref:`ethereum_common/UInt256 <Ethereum-common-UInt256.msg>`   The amount of tokens
=========== ============================================================ ===============================================

**Response**

=========== ============================================================ ===============================================
Field       Type                                                            Description
=========== ============================================================ ===============================================
txhash      std_msgs/Uint8[32]                                              Transaction hash
=========== ============================================================ ===============================================
