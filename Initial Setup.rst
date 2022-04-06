Initial Setup
=============

Installation
------------

The Python Onboard API client is available to install through pip:

   >>> pip install onboard.client

or by cloning our `Github repo <https://github.com/onboard-data/client-py/>`_:

.. code-block:: bash

   git clone git@github.com:onboard-data/client-py

Please note, the client requires Python >= 3.7.

Setting up API access
---------------------

You’ll need an active API Key with the appropriate scopes in order to use this python client.

If you are an existing Onboard user you can head over to the accounts page and generate a new key and grant scopes for “general” and “buildings:read”.

If you would like to get access to Onboard and start prototyping against an example building please `request access here <https://www.onboarddata.io/contact-us>`_.

If you're participating in the `NYSERDA hackathon <https://www.rtemhackathon.com/>`_, please check your confirmation email after signing up for API access instructions.

You can test if your API key is working with the following code:

   >>> from onboard.client import OnboardClient
   >>> client = OnboardClient(api_key='your-api-key-here')
   >>>
   >>> # Verify access & connectivity
   >>> client.whoami()
   {'result': 'ok', 'apiKeyInHeader': True, ... 'authLevel': 4}

You can also retrieve a list of your currently authorized scopes with :code:`client.whoami()['apiKeyScopes']`.
