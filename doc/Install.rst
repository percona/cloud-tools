.. role:: sh(code)
   :language: bash

.. role:: sql(code)
   :language: sql

Installation Guide
##################

.. _Quick Install:

Quick Install
*************

1. `Get your API key. <https://cloud.percona.com/api-key>`_
2. As root, run in the terminal:

:sh:`curl -s https://cloud.percona.com/install | bash /dev/stdin -api-key="<API key>"`

By default a quick install:

* Enables *Server Metrics Monitor*
* Enables *MySQL Metrics Monitor* if MySQL is present
* Enables *MySQL Query Analytics* if MySQL is present and running locally

A quick install requires `MySQL Auto-detection`_ to work properly. If it fails (e.g. it can't connect to MySQL), only *Server Metrics Monitor* is enabled.

.. _Standard Install:

Standard Install
****************

1. `Download the latest percona-agent. <http://www.percona.com/downloads/percona-agent/LATEST/>`_
2. Extract the tarball and change to the directory it creates.
3. Run the :sh:`install` script.

By default, the installer is automatic and interactive: it tries to do everything automatically as in a *Quick Install*, but if it has problems it prompts you for input. You can disable prompts by specifying :sh:`-interactive=false` for an `Automated Install`_.

.. _Automated Install:

Automated Install
*****************

To automate installation of *percona-agent* (e.g. for Chef, Puppet, etc.) add the :sh:`-interacive=false` flag to a `Standard Install`_ to prevent the installer from prompting. A `Quick Install`_ can be used too because it sets :sh:`-interacive=false` by default.

Automation relies on:

* proper `MySQL Auto-detection`_
* or, specifying `MySQL Options`_,
* or, a combination of both

If the installer fails to setup MySQL it will continue and enable only *Server Metrics Monitor*.

For example, without `MySQL Auto-detection`_ you can specify the necessary `MySQL Options`_ instead:

.. code:: sh

   `./install -interactive=false -mysql-user=root -mysql-pass=secret -mysql-socket=/var/run/mysqld/mysqld.sock`

**Note**: An automated install must create the percona-agent MySQL user; you cannot specify an existing MySQL user. This ability will be added in a future version of the installer.

.. _MySQL Auto-detection:

MySQL Auto-detection
********************

The installer uses :sh:`mysql --print-defaults` to auto-detect the local MySQL instance and MySQL super user credentials. To ensure proper auto-detection, make sure :sh:`~/.my.cnf` (for root) has the necessary MySQL options to connect to MySQL as super user, e.g.:

.. code:: sh

   user=root
   password=pass
   socket=/var/run/mysqld/mysqld.sock

MySQL super user credentials are used to create a MySQL user for the agent with these privileges:

* :sql:`SUPER, PROCESS, USAGE, SELECT ON *.* TO 'percona-agent'@HOST`
* :sql:`UPDATE, DELETE, DROP ON performance_schema.* TO 'percona-agent'@HOST`

:code:`HOST` is :code:`localhost` if a socket or :code:`localhost` is used, else :code:`127.0.0.1` if that IP is used, else :code:`%`. Sometimes the privileges are granted to :code:`localhost` and :code:`127.0.0.1`.

The percona-agent MySQL user password is randomly generated and can be viewed later through the web app.

.. _MySQL Options:

MySQL Options
*************

+-------------------+---------+-----------------------------+
| Flag              | Default | Description                 |
+===================+=========+=============================+
|-mysql             | true    | Install for MySQL           |
+-------------------+---------+-----------------------------+
|-create-mysql-user | true    | Create MySQL user for agent |
+-------------------+---------+-----------------------------+
|-mysql-user        |         | MySQL username              |
+-------------------+---------+-----------------------------+
|-mysql-pass        |         | MySQL password              |
+-------------------+---------+-----------------------------+
|-mysql-host        |         | MySQL host                  |
+-------------------+---------+-----------------------------+
|-mysql-port        |         | MySQL port                  |
+-------------------+---------+-----------------------------+
|-mysql-socket      |         | MySQL socket file           |
+-------------------+---------+-----------------------------+

To get list of all flags run :sh:`./install -help`

MySQL options specified on the command line override (take precedence over) MySQL options discovered by `MySQL Auto-detection`_.

Slave Install
*************

To install *percon-agent* on a slave, first install it on the master, then on the slave run the :sh:`install` script with :sh:`-create-mysql-user=false` and it will prompt you for the existing percona-agent MySQL user credentials.

Since this requires a prompt, a slave install does not currently work for an `Automated Install`_.

Non-MySQL Install
*****************

To install *percona-agent* on a server without MySQL (e.g. to monitor only server metrics), use :sh:`-mysql=false`:

.. code:: sh

   ./install -mysql=false

Updating the Agent
******************

With *Quick Install*
====================

When new version is available
  
1. `Get your api-key <https://cloud.percona.com/api-key>`_
2. Run in terminal as root:

:sh:`curl -s https://cloud.percona.com/install | bash /dev/stdin -api-key="<API key>"`

With *Standard Install*
=======================

1. `Download the latest percona-agent <http://www.percona.com/downloads/percona-agent/LATEST/>`_ to your server.
2. Extract the tarball.
3. Run the :sh:`install` script.

Uninstalling the Agent
**********************

First, to stop and remove *percona-agent* from a server, as root run either:

* :sh:`curl -s https://cloud.percona.com/install | bash /dev/stdin -uninstall` (if you did a `Quick Install`_)

or,

* :sh:`./install -uninstall` (if you did a  `Standard Install`_)

Then `delete the agent <https://cloud.percona.com/agents>`_ in the web app.  This removes its configuration and Query Analytics data from Percona Cloud Tools.

You can also `delete any MySQL instances <https://cloud.percona.com/instances/mysql>`_ that the agent was monitoring.

Finally, you drop the percona-agent MySQL user from any MySQL instance the agent was monitoring by executing:

.. code:: sql

   DROP USER 'percona-agent'@'localhost';
   DROP USER 'percona-agent'@'127.0.0.1';
