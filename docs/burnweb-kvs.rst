.. _burnweb-KVS:

=============
BurnWeb KVS
=============

createStore
=====================

.. code-block:: javascript

    burnweb.createToken(storeName [, callback])

Create a new Key-Value Store.

----------
Parameters
----------

1. ``String`` - Key-Value Store name.
2. ``Function`` - (optional) Optional callback.

-------
Returns
-------

``Promise`` returns ``Object`` - Transaction hash, and the created Key-Value Store ID.

  - ``txHash`` - ``Number``: Transaction hash.
  - ``storeId`` - ``Number``: The created Key-Value Store ID.

-------
Example
-------

.. code-block:: javascript

    burnweb.createStore("KVS01").then(console.log);
    > { txHash: "0xaba239fc212acfd893282e8bca573c72d5b5c1cdf99321700f38147510a8fb6d", "0x0c0573302634DC279302f9dD65241C9825FFAC98" }

------------------------------------------------------------------------------

setKeyValue
=====================

.. code-block:: javascript

    burnweb.setKeyValue(storeId, collection, key, value)

Set key-value pair for specified Key-Value Store ID and collection name.

----------
Parameters
----------

1. ``String`` - The Key-Value Store ID.
2. ``String`` - Collection name.
3. ``String`` - Key string.
4. ``String`` - Value string.
5. ``Function`` - (optional) Optional callback.

-------
Returns
-------

``Promise`` returns ``String`` - Transaction hash

-------
Example
-------

.. code-block:: javascript

    burnweb.setKeyValue("0x0c0573302634DC279302f9dD65241C9825FFAC98", "Collection01", "Key001", "Value001")
    .then(console.log);
    > "0xeff8d7b1a4aee0d88be01c58d0d2d1a5a2d12618a27cfcfd76ebd382fdc1bf8c"

------------------------------------------------------------------------------

deleteKeyValue
=====================

.. code-block:: javascript

    burnweb.deleteKeyValue(storeId, collection, key)

Delete key-value pair for specified Key-Value Store ID, collection name, and key string.

----------
Parameters
----------

1. ``String`` - The Key-Value Store ID.
2. ``String`` - Collection name.
3. ``String`` - Key string.
4. ``Function`` - (optional) Optional callback.

-------
Returns
-------

``Promise`` returns ``String`` - Transaction hash

-------
Example
-------

.. code-block:: javascript

    burnweb.deleteKeyValue("0x0c0573302634DC279302f9dD65241C9825FFAC98", "Collection01", "Key001")
    .then(console.log);
    > "0x9695bbd8b1650fa4b5c1916f212076ae1820ad56a34778aa57c669c777460309"

------------------------------------------------------------------------------

getKeyValue
=====================

.. code-block:: javascript

    burnweb.getKeyValue(storeId, collection, key)

Get key-value pair for specified Key-Value Store ID, collection name, and key string.

----------
Parameters
----------

1. ``String`` - The Key-Value Store ID.
2. ``String`` - Collection name.
3. ``String`` - Key string.
4. ``Function`` - (optional) Optional callback.

-------
Returns
-------

``Promise`` returns ``Object`` - The Key-Value object.

  - ``store_id`` - ``String``: The Key-Value Store ID.
  - ``collection`` - ``String``: Collection name.
  - ``key`` - ``String``: Key string.
  - ``value`` - ``String``: Value string.

-------
Example
-------


.. code-block:: javascript

    burnweb.getKeyValue("0x0c0573302634DC279302f9dD65241C9825FFAC98", "Collection01", "Key001")
    .then(console.log);
    > {
        "store_id": "0x0c0573302634DC279302f9dD65241C9825FFAC98",
        "collection": "Collection01",
        "key": "Key001",
        "value": "Value001"
    }