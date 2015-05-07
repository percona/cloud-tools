Configuration
=============

Percona Cloud Tools provides a number of advanced configuration options.
To access PCT configuration, open the **Configure** section of the web UI.

The **Configure** section enables you to manage the following:

* Server instances
* MySQL instances
* Percona Agents
* Email reports

Server Configuration
--------------------

The **Server** tab contains information about all server instances
known to your PCT infrastructure.
For each server, you can open the sysinfo_ with detailed report.

To configure how general server metrics are collected,
click **Server Metrics** for a specific server.
General server metrics include CPU, memory, disk,
and other critical system readings that are not related to MySQL.

The **Server Metrics** dialog enables you to configure
how often Percona Agent collects and reports collected server metrics.
If you do not require metrics to be collected for a server,
click **Stop** to stop the agent service.

When you change necessary settings, click **Apply** to save changes.

MySQL Configuration
-------------------

The **MySQL** tab contains information about all MySQL instances
known to your PCT infrastructure.
For each MySQL instance, you can open the sysinfo_ with detailed report.

Configuring Metrics Monitor
***************************

To configure how MySQL metrics are collected,
click **MySQL Metrics** for a specific MySQL instance.
MySQL metrics are used to populate charts for :doc:`MetricsMonitor`.

To change the agent that collects MySQL metrics,
stop the agent service, and use the **Agent** drop-down list.
To configure how often the agent should collect and report collected metrics,
specify necessary values
in the **Collect interval** and **Report interval** fields.

Select the check boxes for metrics that you want to collect.
When you change necessary settings, click **Apply** to save changes.

Reporting MySQL Configuration
*****************************

MySQL uses configuration files to store operating parameters.
Percona Agent collects these parameters along with other metrics.
By default, they are retrieved using ``SHOW GLOBAL VARIABLES``
and reported every hour.

To change the agent that collects configuration parameters,
stop the agent service, and use the **Agent** drop-down list.
You can also change the reporting interval.

Configuring Query Analytics
***************************

To configure how query data is collected,
click **Query Analytics** for a specific MySQL instance.
Query data is used by the :doc:`QueryAnalytics` module.

By default, query data is reported every minute.
You can change the reporting period if necessary.

There are two methods for collecting data:

* *Slow query log* is the default source of query data.
* *Performance Schema* is a much faster and efficient alternative
  for busy servers.

.. note:: For more information about the advantages and disadvantages
   of Performance Schema over the slow query log,
   see :doc:`PerfSchema`.

If you select to use Performance Schema,
you can run ``TRUNCATE performance_schema.events_statements_summary_by_digest``
when the Query Analytics module starts.
This ensures that there is no invalid SQL code left by third-party tools,
which may not be properly handled by Percona Agent.

The following settings are available for the slow query log:

Long query time
 Queries that take more than the specified time in seconds to execute
 are added to the slow query log.
 By default, it is set to 0, meaning that all queries are considered *long*.

Max slow query log size
 When the slow query log reaches the specified size in bytes,
 a new one is created.
 You can add a letter to the value:

 * K for kilobytes
 * M for megabytes
 * G for gigabytes

 By default, it is set to 1G,
 meaning that the maximum allowed size for the slow query log is one gigabyte.

 If you set it to 0, the log will grow indefinitely.

Remove old slow logs
 Select this option if you want to remove the old slow query log
 when it reaches maximum size and a new one is created.
 Disable this option if you want to keep old logs.

Send your application's actual queries
 Select this option if you want Percona Agent to send real queries.
 Disable this option if you want to send query fingerprints.

Query Analytics for Percona Server
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If you are running Percona Server, there are additional options available
for slow query log processing.
These options enable you to better configure the granularity of the log.

To select the verbosity of the log, choose from the following:

:Minimal: Log only queries with microsecond precision
:Standard: Log queries with microsecond precision and InnoDB statistics
:Full: Log all queries. This is selected by default.

You can select to log slow admin statements and slow slave statements.

The **Log slow rate limit** field defines the fraction of queries to log.
By default, the limit is set to 20,
meaning that only 5% of queries should be logged (every 20th query).

Agent Configuration
-------------------
The **Agent** tab contains information about all Percona Agents
in your PCT infrastructure.
You can see the version and status of agents on all servers.

PCT enables you to remotely control agents as follows:

* Restart agent service
* Stop agent service
* Abort agent service
* Delete agent

To expand agent details, click the **info** link.
Details contain status parameters,
which are regularly collected and refreshed.
The status of the agent is a wealth of important debugging information.

Installation Information
************************

The **Install** tab contains information required for installing Percona Agent.
For instance, you can copy the API key or the full command to install the agent.

For more information, see :doc:`Percona Agent`.

Reports Configuration
---------------------

The **Reports** tab contains settings for receiving regular reports
by email from PCT.
These reports contain a digest of critical performance data
for MySQL instances known to PCT.

To enable reports, select **Enable server query reports**.
If you want weekly reports to be enabled for new MySQL instances
that you add, select **Automatically receive reports for new MySQL instances**.

You can select MySQL instances for which to enable reports.
To keep email clutter to a minimum,
disable reports for servers that are not critical,
enable weekly reports for more important servers,
and enable daily email reports only for the most active servers
where you expect frequent changes and high loads.
