.. highlight:: bash

.. |br| raw:: html
   <br />

.. _install:

================================
Percona Agent Installation Guide
================================

Depending on your needs and preferences,
the following installation types are available:

.. list-table:: Installation Types
   :header-rows: 1

   * - Source
     - :ref:`Web <web>` |br| (cloud.percona.com)
     - :ref:`Package <package>` |br| (``rpm``, ``deb``, ``tar.gz``)
     - :ref:`Repositories <repo>` |br| (``yum`` and ``apt``)
   * - Uses
     - :command:`curl`
     - Install script
     - Package manager
   * - Automated [1]_
     - Yes (only)
     - Yes (by default)
     - Yes
   * - Manual/Interactive [2]_
     - No
     - Yes
     - Yes
   * - Slave [3]_
     - No
     - Yes
     - Yes
   * - Updates [4]_
     - No
     - No
     - Yes

.. [1] Attempts to automatically detect necessary MySQL options
       and configure itself
.. [2] Prompts the user for input
       when it is not able to detect necessary options
.. [3] Can install Percona Agent on slave
.. [4] System-based

.. _web:

Web Install
-----------

This is the fastest way to install the latest version of Percona Agent.
A non-interactive installer is used,
which attempts to configure everything automatically.

1. Get the *API key* at https://cloud.percona.com/api-key.
2. Run the following command as root:

   ::

   $ curl -s https://cloud.percona.com/install | bash /dev/stdin -api-key="<API key>"

The installer attempts to automatically detect necessary MySQL options,
as described in :ref:`sys-req`.
If it fails, the installed Percona Agent will not be able to collect any
MySQL metrics and query data, only general system metrics.

For more control over the installation process, see :ref:`package`.

.. _package:

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
   the archive with the latest Percona Agent distribution.
2. Extract the archive and change to the directory it creates.
3. Run the :file:`./install` script as root.

There are many options that you can pass to the
install script for specific cases:

* `Automated Install`_
* `Slave Install`_
* `Non-MySQL Install`_

For a complete list of options,
run the install script with the ``-help`` option
or see the :ref:`Install Script Options <options>` page.

Automated Install
^^^^^^^^^^^^^^^^^

To automate installation and disable install script prompts,
use the ``-interactive=false`` option.
In this case, installation will be the same as during a `Quick Install`_.

.. note:: In this case, you have to specify the ``-api-key`` option.

If the installer fails to detect necessary MySQL options,
Percona Agent will not be able to collect MySQL metrics and query data,
only general server metrics.
To avoid this, you can pass necessary MySQL options to the install script,
for example:

::

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
for example:

::

 $ ./install -interactive=false -create-mysql-user=false -agent-mysql-user=name -agent-mysql-pass=pass

.. note:: Specifying ``-agent-mysql-user`` automatically
   disables ``-create-mysql-user``.

Non-MySQL Install
^^^^^^^^^^^^^^^^^

If you want to install Percona Agent on a server without MySQL
or you do not want to monitor a particular MySQL instance,
pass the ``-mysql=false`` option to the install script:

::

 $ ./install -mysql=false

In this case, Percona Agent will monitor only general server metrics.

.. _repo:

Percona Software Repositories
-----------------------------

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

   ::

    deb http://repo.percona.com/apt trusty main
    deb-src http://repo.percona.com/apt trusty main

3. Update local cache:

   ::

   $ apt-get update

4. Install the Percona Agent package:

   ::

   $ apt-get install percona-agent

Updating Percona Agent
----------------------

When a new version of Percona Agent is available,
use either :ref:`web` or :ref:`package`.
The install script checks for the currently installed version
and applies necessary updates.

If you installed Percona Agent using a package manager,
as described in :ref:`repo`,
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
     which installs the newest versions of all packages in your system:

     ::

     $ apt-get upgrade

Uninstalling Percona Agent
--------------------------

If you did a :ref:`web`, run the following command:

::

 $ curl -s https://cloud.percona.com/install | bash /dev/stdin -uninstall

If you did a :ref:`package`,
change to the directory where the Percona Agent archive was extracted
and run the following command:

::

 $ ./install -uninstall

To drop the **percona-agent** user from any MySQL instance
that the agent was monitoring, execute the following:

.. code-block:: mysql

 > DROP USER 'percona-agent'@'localhost';
 > DROP USER 'percona-agent'@'127.0.0.1';

To remove the agent's configuration and data from Percona Cloud Tools,
log in and delete the agent at https://cloud.percona.com/agents.

You can also delete any MySQL instances that the agent was monitoring
at https://cloud.percona.com/instances/mysql.