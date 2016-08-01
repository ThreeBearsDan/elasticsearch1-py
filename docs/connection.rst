.. _connection_api:

Connection Layer API
====================

All of the classes reponsible for handling the connection to the Elasticsearch
cluster. The default subclasses used can be overriden by passing parameters to the
:class:`~elasticsearch1.Elasticsearch` class. All of the arguments to the client
will be passed on to :class:`~elasticsearch1.Transport`,
:class:`~elasticsearch1.ConnectionPool` and :class:`~elasticsearch1.Connection`.

For example if you wanted to use your own implementation of the
:class:`~elasticsearch1.ConnectionSelector` class you can just pass in the
``selector_class`` parameter.

.. note::

  :class:`~elasticsearch1.ConnectionPool` and related options (like
  ``selector_class``) will only be used if more than one connection is defined.
  Either directly or via the :ref:`sniffing` mechanism.

.. py:module:: elasticsearch1

Transport
---------

.. autoclass:: Transport(hosts, connection_class=Urllib3HttpConnection, connection_pool_class=ConnectionPool, nodes_to_host_callback=construct_hosts_list, sniff_on_start=False, sniffer_timeout=None, sniff_on_connection_fail=False, serializer=JSONSerializer(), max_retries=3, ** kwargs)
   :members:


Connection Pool
---------------

.. autoclass:: ConnectionPool(connections, dead_timeout=60, selector_class=RoundRobinSelector, randomize_hosts=True, ** kwargs)
   :members:


Connection Selector
-------------------

.. autoclass:: ConnectionSelector(opts)
   :members:


Urllib3HttpConnection (default connection_class)
------------------------------------------------

.. autoclass:: Urllib3HttpConnection
   :members:
