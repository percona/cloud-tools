.. _faq:

Frequently Asked Questions
==========================

.. contents::
   :local:


How to install Percona Agent on Amazon RDS?
-------------------------------------------

This is currently not possible,
because Percona Agent does not support
monitoring multiple remote MySQL instances.
It is a planned feature, which will be available soon.

How to set up Percona Agent to use a proxy server?
--------------------------------------------------

Percona Agent does not support proxies.
It is a planned feature, which will be available soon for
:abbr:`HTTPS (Hypertext Transfer Procol Secure)` proxies.

Which IP addresses does Percona Agent use?
------------------------------------------

Percona Agent communicates using the :abbr:`URI (uniform resource locator)`
specified by the ``link`` entry in
:file:`/usr/local/percona/percona-agent/config/agent.conf`.

Why does Percona Agent fill up disk space?
------------------------------------------

Percona Agent saves collected data to the
:file:`/usr/local/percona/percona-agent/data` folder before sending it to PCT.
If there is a connection issue and it fails to send data,
the agent stores this data until it manages to send it.

What does ``write unix /var/lib/mysql/mysql.sock: broken pipe`` message mean?
-----------------------------------------------------------------------------

If you see messages like this in :file:`percona-agent.log`,
it indicates a connection issue,
and possibly a problem with credentials for the *percona-agent* user
to access MySQL.

First of all, make sure that there is a *percona-agent* user
set up for the MySQL instance.
If it is, try to restart the agent by running the following command::

$ service percona-agent restart

or

::

$ /etc/init.d/percona-agent restart

How to install Percona Agent on a server with old password authentication?
--------------------------------------------------------------------------

If you need to install Percona Agent on a server
with old password authentication, specify the ``-old-passwords=true`` option.

For MySQL 4.1 and later versions,
you may have old passwords enabled explicitely.
In this case, you can disable old passwords on session level:

.. code-block:: mysql

 mysql> SET SESSION old_passwords=0;

Then create the *percona-agent* user and install Percona agent
with the ``-create-mysql-user=false`` option.
