.. highlight:: bash

.. |PCT| replace:: :abbr:`PCT (Percona Cloud Tools)`

Percona Agent
=============

Percona Agent is a background service that collects performance data
and sends it over a secure websocket connection to |PCT|.

Percona Agent code is open source, and available on
`GitHub <https://github.com/percona/percona-agent>`_.

.. _quick-install:

To install Percona Agent:

1. Get the :term:`API key` at https://cloud.percona.com/api-key.
#. Run the following command as **root**:

   ::

   $ curl -s https://cloud.percona.com/install | bash /dev/stdin -api-key="<API key>"

The installer attempts to automatically detect necessary MySQL options,
as described in `System Requirements`_.
If it fails, the installed Percona Agent will not be able to collect any
MySQL metrics and query data, only general system metrics.
For more control over the installation process, see `Package Install`_.

Release Notes
-------------

.. toctree::
  :maxdepth: 1

  release-notes/1.0/1.0.13
  release-notes/1.0/1.0.12
  release-notes/1.0/1.0.11
  release-notes/1.0/1.0.10
  release-notes/1.0/1.0.9
  release-notes/1.0/1.0.8
  release-notes/1.0/1.0.7

System Requirements
-------------------

.. sidebar:: Percona Toolkit

   :term:`Percona Toolkit` is required by Percona Agent
   to provide :term:`System Info`
   with detailed information about the server and MySQL.
   You can find installation instructions in
   `Percona Toolkit Documentation <http://www.percona.com/doc/percona-toolkit>`_

Percona Agent requires the following:

* Any 32-bit or 64-bit Linux distribution with root access
* Outbound connection to \*.percona.com (on ports 80 and 443)

For MySQL metrics monitoring and query analytics:

* MySQL 5.1 or later (if using MySQL :term:`slow query log`)
* MySQL 5.6 or later (if using MySQL :term:`Performance Schema`)

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

Package Install
---------------

.. sidebar:: Specific Version

   Package install can be used to install a specific version of Percona Agent,
   other than the latest.
   For this, select the required version from the drop-down list on the
   `Download page <http://www.percona.com/downloads/percona-agent/>`_.

The Percona Agent distribution package contains an interactive install script
that prompts the user for input when it is not able to detect necessary options.
For example, the script prompts for the
API key, unless you specify it using the ``-api-key`` option.

1. `Download <http://www.percona.com/downloads/percona-agent/LATEST/>`_
   the archive with the latest Percona Agent distribution package.
#. Extract the archive and change to the directory it creates.
#. Run the :file:`./install` script as **root**.

There are many options that you can pass to the
install script for specific cases:

* `Automated Install`_
* `Slave Install`_
* `Non-MySQL Install`_

For a complete list of options,
run the install script with the ``-help`` option
or see the `Install Script Options`_ reference section.

Automated Install
^^^^^^^^^^^^^^^^^

To automate installation and disable install script prompts,
use the ``-interactive=false`` option.
In this case, installation will be the same as during a
:ref:`Quick Install <quick-install>`.

.. note:: If you run the install script in non-interactive mode,
   you have to specify the ``-api-key`` option.

If the installer fails to detect necessary MySQL options,
Percona Agent will not be able to collect MySQL metrics and query data,
only general system metrics.
To avoid this, you can pass necessary MySQL options to the install script,
for example::

$ ./install -interactive=false -api-key=1a2b3c -mysql-user=root -mysql-pass=pass -mysql-socket=/var/run/mysqld/mysqld.sock

Slave Install
^^^^^^^^^^^^^

After you install Percona Agent on the master,
run the install script with the ``-create-mysql-user=false``
option on the slave.
In this case, the install script will prompt you for
existing Percona Agent user credentials on MySQL.

To install Percona Agent on the slave in automated mode,
specify the agent's MySQL user credentials as options for the install script,
for example::

$ ./install -interactive=false -create-mysql-user=false -agent-mysql-user=name -agent-mysql-pass=pass

.. note:: Specifying ``-agent-mysql-user`` automatically
   disables ``-create-mysql-user``.

Non-MySQL Install
^^^^^^^^^^^^^^^^^

If you want to install Percona Agent on a server without MySQL
or you do not want to monitor a particular MySQL instance,
pass the ``-mysql=false`` option to the install script::

$ ./install -mysql=false

In this case, Percona Agent will monitor only general system metrics.

Using Percona Software Repositories
-----------------------------------

Percona provides repositories for popular package managers:

* :command:`yum` (RPM packages for RedHat, CentOS, Amazon Linux AMI, etc.)
* :command:`apt` (.deb packages for Debian, Ubuntu, etc.)

You can use those package managers to install and update all Percona software
with any dependencies.

Installing on RPM-based systems
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

To install Percona Agent using the :command:`yum` manager:

1. Install an RPM that configures :command:`yum` and installs the
   `Percona GPG key <http://www.percona.com/downloads/RPM-GPG-KEY-percona>`_:

   ::

   $ yum install http://www.percona.com/downloads/percona-release/redhat/0.1-3/percona-release-0.1-3.noarch.rpm

2. Make sure that Percona packages are available from the repository:

   ::

   $ yum list | grep percona

3. Install the Percona Agent package:

   ::

   $ yum install percona-agent

Installing on Debian-based systems
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

To install using the :command:`apt` manager:

1. Add Percona package key to :command:`apt`:

   ::

   $ apt-key adv --keyserver keys.gnupg.net --recv-keys 1C4CBDCDCD2EFD2A

2. Add Percona repository sources to :file:`/etc/apt/sources.list`
   with the correct name of the distribution.
   For example, if you are running Ubuntu 14.04 (Trusty Tahr),
   add the following lines:

   .. code-block:: none

      deb http://repo.percona.com/apt trusty main
      deb-src http://repo.percona.com/apt trusty main

3. Update local cache:

   ::

   $ apt-get update

4. Install the Percona Agent package:

   ::

   $ apt-get install percona-agent

Managing Percona Agent
----------------------

After installation,
Percona Agent is started and run in the background as a service.
You can control the :command:`percona-agent` service as follows::

$ sudo /etc/init.d/percona-agent {start|stop|restart|status}

Alternatively, use the following::

$ sudo service percona-agent {start|stop|restart|status}

Updating Percona Agent
----------------------

When a new version of Percona Agent is available,
use either :ref:`Quick Install <quick-install>` or `Package Install`_ to update.
The install script checks for the currently installed version
and applies necessary updates.

If you installed Percona Agent using a package manager,
as described in `Using Percona Software Repositories`_,
then you can update it as follows:

* For :command:`yum`, run the following command:

  ::

  $ yum update percona-agent

  .. note:: You can run the previous command
     without specifying the ``percona-agent`` package
     to make :command:`yum` update all installed packages.

* For :command:`apt`, run the following command:

  ::

  $ apt-get install --only-upgrade percona-agent

  .. note:: You can also run the following command,
     which installs the newest versions of all packages installed on the system:

     ::

     $ apt-get upgrade

Uninstalling Percona Agent
--------------------------

If you did a :ref:`Quick Install <quick-install>`,
run the following command to uninstall Percona Agent::

$ curl -s https://cloud.percona.com/install | bash /dev/stdin -uninstall

If you did a `Package Install`_,
change to the directory where the Percona Agent archive was extracted
and run the following command::

$ ./install -uninstall

To drop the Percona Agent user from any MySQL instance
that the agent was monitoring,
execute the following on the MySQL server:

.. code-block:: mysql

 > DROP USER 'percona-agent'@'localhost';
 > DROP USER 'percona-agent'@'127.0.0.1';

To remove the agent's configuration and data from Percona Cloud Tools,
log in and delete the agent at https://cloud.percona.com/agents.

You can also delete any MySQL instances that the agent was monitoring
at https://cloud.percona.com/instances/mysql.

Install Script Options
----------------------

You can pass command-line options to the Percona Agent install script
in special cases.
For example, the installer may not be able to detect necessary MySQL options,
or you may want the installer to perform non-standard procedures.

The general syntax for most options is the name of the option,
followed by the equals sign and the argument value:

:samp:`{OPTION}={ARG}`

Arguments can be one of the following types:

:Boolean: Specify either ``true`` or ``false`` to enable or disable something.
:String: Specify a string of characters, such as a name or an address.
 If the string contains spaces, enclose it in quotation marks.
:Integer: Specify an integer number.

Some options do not have arguments,
you simply specify the option to enable something.

To get a list of install script options with short descriptions,
run the install script with the ``-help`` option.

.. _agent-mysql-pass:

**-agent-mysql-pass**
  Specify existing MySQL user password for Percona Agent.

  See also: :ref:`-create-mysql-user <create-mysql-user>`

.. _agent-mysql-user:

**-agent-mysql-user**
  Specify existing MySQL user name for Percona Agent.

  See also: :ref:`-create-mysql-user <create-mysql-user>`

.. _api-host:

**-api-host**
  Specify the host for accessing the Percona Cloud API.

  Default: ``-api-host=cloud-api.percona.com``

.. _api-key:

**-api-key**
  Specify the unique API key for your organization.
  You can find it at https://cloud.percona.com/api-key

.. _auto-detect_mysql:

**-auto-detect-mysql**
  Set to ``false`` if you do not want the Percona Agent installer
  to detect local MySQL instance and MySQL user credentials
  using :command:`mysql --print-defaults`.
  For more information, see `System Requirements`_.

  Default: ``-auto-detect-mysql=true``

.. _basedir:

**-basedir**
  Specify the base directory for installing Percona Agent.

  Default: ``-basedir=/usr/local/percona/percona-agent``

.. _create-agent:

**-create-agent**
  Set to ``false`` if you do not want to create an agent instance
  in Percona Cloud Tools.

  Default: ``-create-agent=true``

.. _create-mysql-instance:

**-create-mysql-instance**
  Set to ``false`` if you do not want to create a MySQL instance
  in Percona Cloud Tools.

  Default: ``-create-mysql-instance=true``

  See also: :ref:`-mysql <mysql>`

.. _create-mysql-user:

**-create-mysql-user**
  Set to ``false`` if you do not want to create a MySQL user for Percona Agent.
  For example, if a user already exists for Percona Agent
  that monitors the master MySQL instance,
  specify its credentials when installing Percona Agent for slave.

  Default: ``-create-mysql-user=true``

  See also: :ref:`-agent-mysql-pass <agent-mysql-pass>`,
  :ref:`-agent-mysql-user <agent-mysql-user>`

.. _create-server-instance:

**-create-server-instance**
  Set to ``false`` if you do not want to create a server instance
  in Percona Cloud Tools.

  Default: ``-create-server-instance=true``

.. _debug:

**-debug**
  Set to ``true`` if you want to enable debugging.

  Default: ``-debug=false``

.. _help:

**-help**
  Print list of options with short descriptions and exit.

.. _insteractive:

**-interactive**
  Set to ``false`` if you do not want the installer to prompt for input on :file:`stdin`.
  In this case, you have to specify at least the ``-api-key`` option.
  For more information see `Automated Install`_.

  Default: ``-interactive=true``

.. _mysql:

**-mysql**
  Set to ``false`` if installing Percona Agent on a server without MySQL
  or if you do not want to monitor MySQL metrics and query data.
  In this case, Percona Agent will monitor only general server metrics
  and MySQL instance will not be created in Percona Cloud Tools.

  Setting ``-mysql=false`` is the same as setting the following two options:

  * ``-create-mysql-instance=false``
  * ``-start-mysql-service=false``

  Default: ``-mysql=true``

.. _mysql-defaults-file:

**-mysql-defaults-file**
  Specify path to the :file:`my.cnf` file,
  which contains necessary MySQL instance options,
  such as the super user credentials and socket.
  By default, these options are read from the following files
  in the given order:

  * :file:`/etc/my.cnf`
  * :file:`/etc/mysql/my.cnf`
  * :file:`/usr/local/mysql/etc/my.cnf`
  * :file:`~/my.cnf`

.. _mysql-host:

**-mysql-host**
  Specify MySQL host.

.. _mysql-max-user-connections:

**-mysql-max-user-connections**
  Specify maximum allowed number of user connections to MySQL.

  Default: ``-mysql-max-user-connections=5``

.. _mysql-pass:

**-mysql-pass**
  Specify MySQL superuser password.

.. _mysql-port:

**-mysql-port**
  Specify MySQL port.

.. _mysql-socket:

**-mysql-socket**
  Specify MySQL socket file.

.. _mysql-user:

**-mysql-user**
  Specify MySQL superuser name.

.. _old-passwords:

**-old-passwords**
  Set to ``true`` if using the original hashing method.
  It was used in MySQL before version 4.1, and produced a 16-byte string,
  instead of 41-byte strings produced by version 4.1 and later.

  Default: ``-old-passwords=false``

.. _start-mysql-services:

**-start-mysql-services**
  Set to ``false`` if you do not want Percona Agent to monitor any activity
  related to MySQL.

  Default: ``-start-mysql-services=true``

  See also: :ref:`-mysql <mysql>`

.. _start-services:

**-start-services**
  Set to ``false`` if you do not want Percona Agent to monitor
  general server performance.

  Default: ``-start-services=true``

.. _uninstall:

**-uninstall**
  Instruct the install script to remove Percona Agent.
