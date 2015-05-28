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

Does Percona Agent store data locally?
------------------------------------------

Percona Agent aggregates collected data in the
:file:`/usr/local/percona/percona-agent/data` folder.
It usually reports collected data in regular intervals,
but if there is a connection issue,
this data is stored until the agent manages to send it.

As of Percona Agent 1.0.13, the following limits apply to local data:

* 1 hour
* 10 MiB
* 100 files

Previous versions did not limit the size of the :file:`data` folder,
which lead to situations when Percona Agent filled up disk space indefinitely.

What does ``write unix /var/lib/mysql/mysql.sock: broken pipe`` message mean?
-----------------------------------------------------------------------------

Messages in :file:`percona-agent.log` are not necessarily from Percona Agent.
This file is used to capture many various messages.

You should refer to the agent log in the web UI
for specific Percona Agent errors.
To view the agent log, open **Configure** > **Agent**,
and click **info** for the agent you want to troubleshoot.
For more information, see :ref:`agent-config`.

This particular message is from the Go MySQL driver.
It indicates a connection issue,
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
In this case, you can disable old passwords for one session
while you install Percona Agent:

.. code-block:: mysql

 mysql> SET SESSION old_passwords=0;

Then create the *percona-agent* user and install Percona agent
with the ``-create-mysql-user=false`` option.
