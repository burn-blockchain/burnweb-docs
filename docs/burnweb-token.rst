.. _burnweb-token:

=============
BurnWeb Token
=============

getToken
=====================

.. code-block:: javascript

    burnweb.getToken(tokenId [, callback])

Get the token information.

----------
Parameters
----------

1. ``String`` - The token ID.
2. ``Function`` - (optional) Optional callback.

-------
Returns
-------

``Promise`` returns ``Object`` - The token object.

  - ``token_id`` - ``String``: The token ID.
  - ``owner`` - ``String``: The token owner.
  - ``name`` - ``String``: Token name.
  - ``symbol`` - ``String``: Token symbol.
  - ``decimals`` - ``Number``: Token's decimal place.
  - ``total_supply`` - ``String``: Current total supply of the token.
  - ``mintable`` - ``Number``: 0 or 1 (0: not mintable, 1: mintable)
  - ``burnable`` - ``Number``: 0 or 1 (0: not burnable, 1: burnable)
  - ``icon`` - ``String``: URL to the token icon image.
  - ``tx_fee`` - ``String``: See details at :ref:`Transaction Fee <tx-fee>` 
  - ``tx_fee_rate`` - ``String``: See details at :ref:`Transaction Fee <tx-fee>` 
  - ``created`` - ``DateTime``: The token created date time formatted in 'YYYY-MM-DD HH:mm:ss'

-------
Example
-------


.. code-block:: javascript

    burnweb.getBlock(1234)
    .then(console.log);
    > {
        "token_id": "0x004b1d45cbd495aae40bc921e318d27fffb1d357",
        "owner": "0x3a762d996bbb3633c653e1dcb0201663874dc9e2",
        "name": "Name",
        "symbol": "USDN",
        "decimals": 6,
        "total_supply": "20000000000000",
        "mintable": 1,
        "burnable": 0,
        "icon": "https://s3.aws.com/11980234/219315.png",
        "tx_fee": "0",
        "tx_fee_rate": "0",
        "created": "2020-11-16 11:17:50"
    }

------------------------------------------------------------------------------

getBalanceOf
=====================

.. code-block:: javascript

    burnweb.getBalance(tokenId, address [, callback])

Get the token balance of a specified address.

----------
Parameters
----------

1. ``String`` - The token ID.
2. ``String`` - The address to get the balance of the token.
3. ``Function`` - (optional) Optional callback.

-------
Returns
-------

``Promise`` returns ``String`` - The current balance of the token for the given address

-------
Example
-------

.. code-block:: javascript

    burnweb.getBalanceOf("0x003d6e501a19921a63a9046f5da10675bc0965b2", "0xa1d8ba23b27c334b01b6260a2eb6d767fa035cb2")
    .then(console.log);
    > "1000000000000"

------------------------------------------------------------------------------

createToken
=====================

.. code-block:: javascript

    burnweb.createToken(
        name,
        symbol,
        decimals,
        totalSupply,
        feeToken,
        txFee,
        txFeeRate,
        icon,
        mintable,
        burnable
        [, callback]
    )

Create a new token.

----------
Parameters
----------

1. ``String`` - Token name.
2. ``String`` - Token symbol.
3. ``Number`` - Token's decimal place.
4. ``String`` - Initial total supply of the token.
5. ``Number`` - 0 or 1 (0: Transaction fee is charged in the native token, 1: Transaction fee is charged in the token itself) 
6. ``String`` - Minimum transaction fee for token transfer. See detials at :ref:`Transaction Fee <tx-fee>` 
7. ``String`` - Transaction fee in rate to transferred token amount. See detials at :ref:`Transaction Fee <tx-fee>` 
8. ``String`` - URL to the token icon image.
9. ``Number`` - 0 or 1 (0: not mintable, 1: mintable)
10. ``Number`` - 0 or 1 (0: not burnable, 1: burnable)
11. ``Function`` - (optional) Optional callback.

-------
Returns
-------

``Promise`` returns ``Object`` - Transaction hash, and the created token ID.

  - ``txHash`` - ``Number``: Transaction hash.
  - ``tokenId`` - ``Number``: The created token ID.

-------
Example
-------

.. code-block:: javascript

    burnweb.getBalanceOf(
        "Alpha USD",
        "USDA",
        18,
        "20000000000000000000000000",
        "0x0000000000000000000000000000000000000000",
        "0",
        "0",
        "icon": "https://burn-network.io/images/udsa.png",
        "mintable": 1,
        "burnable": 0
    ).then(console.log);
    > { txHash: "0xaba239fc212acfd893282e8bca573c72d5b5c1cdf99321700f38147510a8fb6d", "0x97BcC3F68DBcAe2382308C46A59b76fA2f8116f8" }

------------------------------------------------------------------------------

transferToken
=====================

.. code-block:: javascript

    burnweb.transferToken(tokenId, to, amount [, callback])

Transfer token to another address.

----------
Parameters
----------

1. ``String`` - The token ID.
2. ``String`` - Transfer the token to this address.
3. ``String`` - The token amount to transfer.
4. ``Function`` - (optional) Optional callback.

-------
Returns
-------

``Promise`` returns ``String`` - Transaction hash

-------
Example
-------

.. code-block:: javascript

    burnweb.transferToken("0x97bcc3f68dbcae2382308c46a59b76fa2f8116f8", "0xa2710da45f1343c9ee2f88d0e64ea0c8aaadfeff", "20000")
    .then(console.log);
    > "0xaba239fc212acfd893282e8bca573c72d5b5c1cdf99321700f38147510a8fb6d"

------------------------------------------------------------------------------

issueToken
=====================

.. code-block:: javascript

    burnweb.issueToken(tokenId, to, amount)

Issue (mint) token to a specified address.

----------
Parameters
----------

1. ``String`` - The token ID.
2. ``String`` - The address to which the token is issued.
3. ``String`` - Token amount to issue.
4. ``Function`` - (optional) Optional callback.

-------
Returns
-------

``Promise`` returns ``String`` - Transaction hash

-------
Example
-------

.. code-block:: javascript

    burnweb.issueToken("0x97BcC3F68DBcAe2382308C46A59b76fA2f8116f8", "0xa2710da45f1343c9ee2f88d0e64ea0c8aaadfeff", "1000000000000000000000000")
    .then(console.log);
    > "0x84dd7f59a662fa159808881a60a669319fd0366006b8c8c3d293860abc4b46da"

------------------------------------------------------------------------------

burnToken
=====================

.. code-block:: javascript

    burnweb.burnToken(tokenId, amount)

Burn token balance.

----------
Parameters
----------

1. ``String`` - The token ID.
2. ``String`` - Token amount to burn. 
3. ``Function`` - (optional) Optional callback.

-------
Returns
-------

``Promise`` returns ``String`` - Transaction hash

-------
Example
-------

.. code-block:: javascript

    burnweb.burnToken("0x97BcC3F68DBcAe2382308C46A59b76fA2f8116f8", "100000000000000000000")
    .then(console.log);
    > "0xe0509cc9e9569a693e38246cffaeb3997d44167c9cc2500088505cd68abe9d23"

------------------------------------------------------------------------------

listTokenTransactions
=====================

.. code-block:: javascript

    burnweb.listTokenTransactions(tokenId, from, to, start, end [, callback])

List transactions for specified token.

----------
Parameters
----------

1. ``String`` - The token ID.
2. ``String`` - (optional) Token sender
3. ``String`` - (optional) Token receiver
4. ``String`` - DateTime range start (e.g. "2021-02-15 07:52:37")
5. ``String`` - DateTime range end (e.g. "2025-02-15 01:00:00")
6. ``Function`` - (optional) Optional callback.

-------
Returns
-------

``Promise`` returns ``Object`` - The list of transaction object.

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

    burnweb.listTokenTransactions("0x0000000000000000000000000000000000000000", undefined, undefined, "2021-02-15 00:0:00", "9999-01-01 00:00:00")
    .then(console.log);
    > [
        {
          "tx_id": "0x335341f1cba6eb17b7c6cbf76d59db5a8ba4f936cd88977892c704b089f0b91a",
          "block_number": "8898401",
          "nonce": "388348616525703",
          "token_id": "0x0000000000000000000000000000000000000000",
          "source": "0x4bea9f4ebba2c63289fb257ed58df1e0e572b1e4",
          "target": "0x93106e4f822ec69776f8fa8dfa514701308cd510",
          "amount": "1100000000000000000",
          "fee": "100",
          "data": "",
          "signature": "8422d2f46d65626f0be85788d8595135fbf4af048b1a77fa00495ff9ba17b6bc94ee66066ed5b64217c57a727f3ce833a3be2e310723b6bf4c68bb45c07e23ccf9af2f",
          "created": "2021-02-15 07:52:46"
        }
      ]