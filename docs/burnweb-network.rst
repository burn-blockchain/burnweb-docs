.. _burnweb-network:

===============
BurnWeb Network
===============

This is the main class of the burnweb library.

.. code-block:: javascript

    var BurnWeb = require('burnweb');

    // Set BURN endpoint URL to initialize
    var burnweb = new BurnWeb('http://localhost:8545');

    // or, specify private key at the same time
    var burnweb = new BurnWeb('http://localhost:8545', privateKey);

------------------------------------------------------------------------------

getBlockNumber
=====================

.. code-block:: javascript

    burnweb.getBlockNumber([callback])

Returns the current block number.

-------
Returns
-------

``Promise`` returns ``Number`` - The latest block number.

-------
Example
-------


.. code-block:: javascript

    burnweb.getBlockNumber()
    .then(console.log);
    > 1234

------------------------------------------------------------------------------

.. _get-block:

getBlock
=====================

.. code-block:: javascript

    burnweb.getBlock(blockNumber [, callback])

Returns a block information for the specified block number.

----------
Parameters
----------

1. ``Number|BN|BigNumber`` - The block number.
2. ``Function`` - (optional) Optional callback.

-------
Returns
-------


``Promise`` returns ``Object`` - The block object:

  - ``block_number`` - ``Number``: The block number. ``null`` if a pending block.
  - ``checkpoint_number`` - ``Number``: The block number. ``null`` if a pending block.
  - ``parent_hash`` 32 Bytes - ``String``: Hash of the parent block.
  - ``tx_root_hash`` 32 Bytes - ``String``: Merkle hash of the transactions.
  - ``block_hash`` 32 Bytes - ``String``: Hash of the current block.
  - ``created`` - ``DateTime``: The block created date time formatted in 'YYYY-MM-DD HH:mm:ss'

-------
Example
-------


.. code-block:: javascript

    burnweb.getBlock(1234)
    .then(console.log);
    > {
        "block_number": 1234,
        "checkpoint_number": 123,
        "parent_hash": "0x10dd40dd6d96d36897d01c38a7047f17920f8eefe05af01800ba07c0be269099",
        "tx_root_hash": "0x0bf84e5a9a443c22eb4a7d1446213ed67da18b64a1fbcad3f50e699f4d2233cb",
        "block_hash": "0x7901d33b19010f009bb1fb8c31d7f522ebced81188bf9e4f3255e8c5c47cacbc",
        "created": "2020-08-02 10:02:11"
    }

------------------------------------------------------------------------------

getBalance
=====================

.. code-block:: javascript

    burnweb.getBalance(address [, callback])

Get the native token balance of a specified address.

----------
Parameters
----------

1. ``String`` - The address to get the balance of native token.
2. ``Function`` - (optional) Optional callback.

-------
Returns
-------

``Promise`` returns ``String`` - The current balance for the given address

-------
Example
-------

.. code-block:: javascript

    burnweb.getBalance("0xa1d8ba23b27c334b01b6260a2eb6d767fa035cb2")
    .then(console.log);
    > "1000000000000"

------------------------------------------------------------------------------

getTransaction
=====================

.. code-block:: javascript

    burnweb.getTransaction(tx_hash [, callback])

Returns a transaction details for a specified tx hash.

----------
Parameters
----------

1. ``String`` - The transaction hash.
2. ``Function`` - (optional) Optional callback.

-------
Returns
-------

``Promise`` returns ``Object`` - The transaction object:

  - ``tx_id`` 32 Bytes - ``String``: Hash of the transaction.
  - ``block_number`` - ``Number``: The block number where the transaction is included.
  - ``nonce`` - ``Number``: Unique number for the transaction.
  - ``token_id`` - ``String``: If token transfer transaction, the token id of the transferred token.
  - ``source`` - ``String``: If token transfer transaction, the addresss of the token sender.
  - ``target`` - ``String``: If token transfer transaction, the addresss of the token receiver.
  - ``amount`` - ``Number``: If token transfer transaction, the amount of token transferred.
  - ``fee`` - ``Number``: Transaction fee deducted. See :ref:`fee <tx-fee>` for more details.
  - ``data`` - ``String``: RLP endoded parameters. See :ref:`data <tx-data>` for more details.
  - ``signature`` - ``String``: Transaction signature. See :ref:`signature <tx-hash-signature>` for more details.
  - ``created`` - ``DateTime``: The transaction created date time formatted in 'YYYY-MM-DD HH:mm:ss'

-------
Example
-------

.. code-block:: javascript

    burnweb.getTransaction('0x9fc76417374aa880d4449a1f7f31ec597f00b1f6f3dd2d66f4c9c6c445836d8b§234')
    .then(console.log);
    > {
        "tx_id": "0x4c095d0b9746625158ac68352f32f4af69d8b35dbb54fdac03c487b887de32ee",
        "block_number": 26,
        "nonce": 38706715,
        "token_id": "0xb02d1e0a6680bb1f236acddc4d1797dad9e0041e",
        "source": "0xa2710da45f1343c9ee2f88d0e64ea0c8aaadfeff",
        "target": "0x50B192630d0685570e1DBECAF045011bec139b14",
        "amount": 1000,
        "fee": 0,
        "data": null,
        "signature": "25a0873e52000b760903e922fe3dde6dd895b1e88afb4f379633a4d74351b5ddba183fba1ccbdebf46ab0fb7f8632a94442b58522dee3928f75a37d589a6156c33",
        "created": "2020-09-24 03:31:57",
    }
