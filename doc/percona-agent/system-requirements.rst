.. _sys-req:

=================================
Percona Agent System Requirements
=================================

.. sidebar:: Percona Toolkit

   :term:`Percona Toolkit` is required by Percona Agent
   to provide :term:`System Info`
   with detailed information about the host system and MySQL server.
   You can find installation instructions in
   `Percona Toolkit Documentation <http://www.percona.com/doc/percona-toolkit>`_

Percona Agent requires the following:

* Any 32-bit or 64-bit Linux distribution with root access
* Outbound connection to \*.percona.com (on ports 80 and 443)

For MySQL metrics monitoring and query analytics:

* MySQL 5.1 or later (if using the :term:`slow query log`)
* MySQL 5.6 or later (if using :term:`Performance Schema`)

.. note:: For more information about the advantages and
  disadvantages of Performance Schema over slow query log,
  see :ref:`perf-schema`.

The Percona Agent installer uses :command:`mysql --print-defaults`
to detect local MySQL instance and MySQL superuser credentials.
Make sure that the necessary options are specified in :file:`~/.my.cnf`
(for root). For example:

.. code-block:: none

   user=root
   password=pass
   socket=/var/run/mysqld/mysqld.sock

MySQL superuser credentials are used to create a MySQL user for Percona Agent
with the following privileges:

* ``SUPER, PROCESS, USAGE, SELECT ON *.* TO 'percona-agent'@'localhost'``
* ``UPDATE, DELETE, DROP ON performance_schema.* TO 'percona-agent'@'localhost'``

.. note:: Instead of ``localhost``, a specific IP (such as ``127.0.0.1``)
   or the ``%`` wildcard can be used.

Feature Matrix (TBD)
--------------------

.. list-table:: Features supported by various versions of Percona Agent
   :header-rows: 1

   * - 
     - 1.0.13
     - 1.0.12
     - 1.0.11
   * - old_passwords
     - Yes
     - Yes
     - Yes
   * - Table Info
     - Yes
     - No
     - No
