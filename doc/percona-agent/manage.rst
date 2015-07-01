.. |PCT| replace:: :abbr:`PCT (Percona Cloud Tools)`

.. _manage-agent:

===============================
Managing Percona Agent Instance
===============================

During installation, an instance of Percona Agent is added to |PCT|,
which corresponds to the :command:`percona-agent` service that runs on the host.

You can control the service remotely, without logging in to the host:

1. In |PCT|, select the organization above the instance tree.
2. Expand the host and select the Percona Agent instance.
3. Use the buttons to control the :command:`percona-agent` service:

   :Restart: Restart the service
   :Stop/Start: Stop or start the service
   :Abort: Kill the service
   :Remove: Remove Percona Agent from the host

.. note:: If you log in to the host,
   you can control the :command:`percona-agent` service as follows:

   ::

    $ sudo /etc/init.d/percona-agent {start|stop|restart|status}

   Alternatively, use the following:

   ::

    $ sudo service percona-agent {start|stop|restart|status}

Real-time Status
----------------

The **Status** panel for a Percona Agent instance in |PCT|
contains *real-time status information*.
There is status information available about every part of the agent.

.. image:: images/config-agent-details.png

By default, status is requested and updated every 5 seconds.
To disable status updates, click **Disable autorefresh**.

Online Logs
-----------

The **Logs** panel for a Percona Agent instance in |PCT|
contains messages logged by the agent.

.. image:: images/config-agent-logs.png

You can filter logged messages down by the required level of importance: 

:Error: Messages about events that are fatal to an operation
:Warning: Messages about events that can lead to unexpected behavior,
  or cause an error if no action is taken
:Notice: Messages about unusual events
:Info: Messages about normal operational events
:Debug: Messages useful for developers who want to debug Percona Agent

To disable updates of the log, click **Disable autorefresh**.

To configure log settings,
open the **Configuration** tab for a Percona Agent instance.

.. image:: images/config-agent-log-settings.png

By default, Percona Agent sends log messages to PCT,
rather than saving them locally.
This enables any user in your :term:`organization` to view log messages,
even if they do not have access to the server where Percona Agent is running.

However, there is a local log file used by Percona Agent:
:file:`/usr/local/percona/percona-agent/percona-agent.log`

To enable logging to this file, select **Enable Log File**.

The **Level** drop-down list defines how detailed
you would like the log file to be.
For example, selecting **Info** will include
*Error*, *Warning*, *Notice*, and *Info* message types.