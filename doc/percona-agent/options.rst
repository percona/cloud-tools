.. _options:

====================================
Percona Agent Install Script Options
====================================

You can pass command-line options to the Percona Agent install script
in special cases.
For example, the installer may not be able to detect necessary MySQL options,
or you may want the installer to perform non-standard procedures.

For more information, see :ref:`package`.

The general syntax for most options is the name of the option,
followed by the equals sign and the argument value:

:samp:`{option}={arg}`

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
  using :command:`mysql --print-defaults`,
  as described in :ref:`sys-req`.

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
  In this case, you have to specify at least the ``-api-key`` option,
  as during a :ref:`web`.

  For more information, see :ref:`automated`.

  Default: ``-interactive=true``

.. _mysql:

**-mysql**
  Set to ``false`` if installing Percona Agent on a server without MySQL
  or if you do not want to monitor MySQL metrics and query data.
  In this case, Percona Agent will monitor only general system metrics,
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