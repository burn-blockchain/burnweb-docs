.. _getting-started:

===============
Getting Started
===============

burnweb is a library for interacting with BURN blockchain via REST API.

.. _install-burnweb:

Install burnweb
===============

- Install the `burnweb` package by npm command

.. code-block:: javascript

    npm install git+https://github.com/{your_repository}/burnweb.git

- Create a burnweb instance with a provider (BURN endpooint) specified.

.. code-block:: javascript

    // For js
    var BurnWeb = require('burnweb');
    
    // For ts
    import BurnWeb from 'burnweb';;

    // Set BURN endpoint URL to initialize
    var burnweb = new BurnWeb('http://localhost:8545');

    // or, specify private key at the same time
    var burnweb = new BurnWeb('http://localhost:8545', privateKey);
