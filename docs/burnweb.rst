.. _burnweb:

=======
BurnWeb
=======

This is the main class of the burnweb library. This page shows static methods.

.. code-block:: javascript

    var BurnWeb = require('burnweb');

------------------------------------------------------------------------------

generateAccount
=====================

.. code-block:: javascript

    const account = BurnWeb.generateAccount([entropy]);

Returns random private key and account address.

----------
Parameters
----------

1. ``String`` - (Optional) Random seed string to add entropy.

-------
Returns
-------

``Object``- A pair of private key and account address.

  - ``address`` - ``String``: The derived account address from the private key.
  - ``privateKey`` - ``String``: The specified private key.

-------
Example
-------


.. code-block:: javascript

    BurnWeb.generateAccount()
    > {
        address: '0x61ecf32a6286f91f765645c4bf2d5dde7775b907',
        privateKey: '0x93cd9c0e9ef8ac5eac8552c1b2379e17b1aa569e7f5a50bae9e80d07999abd15'
    }

------------------------------------------------------------------------------

privateKeyToAccount
=====================

.. code-block:: javascript

    const account = BurnWeb.privateKeyToAccount(privateKey);

Returns a derived account address from the specified private key.

----------
Parameters
----------

1. ``String`` - The private key.

-------
Returns
-------

``Object`` - The account address derived from the private key. 

  - ``address`` - ``String``: The derived account address from the private key.
  - ``privateKey`` - ``String``: The specified private key.

-------
Example
-------

.. code-block:: javascript

    BurnWeb.privateKeyToAccount('0x93cd9c0e9ef8ac5eac8552c1b2379e17b1aa569e7f5a50bae9e80d07999abd15')
    > {
        address: '0x61ecf32a6286f91f765645c4bf2d5dde7775b907',
        privateKey: '0x93cd9c0e9ef8ac5eac8552c1b2379e17b1aa569e7f5a50bae9e80d07999abd15' }
    }