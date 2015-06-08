.. _glossary:

Glossary
========

The following is a list of terms related to Percona Cloud Tools (PCT).

.. glossary::

   API key
    A unique key used by :term:`Percona Agent` to identify the data it collects
    as belonging to the corresponding :term:`organization`.
    If you have a :term:`PCT Account`, you can find the API key at
    https://cloud.percona.com/api-key

    .. note:: Make sure that the correct organization is selected.

   Metrics Monitor
    A tool used for presenting collected MySQL and system metrics
    on time-based charts.

    For more information, see the :doc:`MetricsMonitor` section.

   organization
    An entity in PCT that defines all infrustructure components
    and people involved. When you sign up for a :term:`PCT Account`,
    a default organization is created. You can add other
    :term:`users <user>` to the organization, create other organizations,
    or be added to existing organizations.

    Each organization is assigned a unique :term:`API key`,
    which is used by :term:`Percona Agent` to identify the data it collects.
    During installation, :term:`Percona Agent` adds corresponding server
    and MySQL instances to the organization.

   PCT Account
    A user account on `cloud.percona.com <https://cloud.percona.com>`_.

    For more information, see the :doc:`Account` section.

   Percona Agent
    A service that runs on the server,
    collects data about perfomance and MySQL metrics,
    and sends it to PCT.

    For more information, see the :doc:`Agent` section.
..
   Percona Cloud
    Internal infrastructure at the heart of PCT, hosted by Percona.
    In simple terms, it consists of an API server and a database server.
    The API is built to enable both :term:`Percona Agent`
    and :term:`Percona Console` to interact with the database
    of collected metrics.
..
   Percona Console
    Web-based graphical user interface (web GUI)
    that enables users to access data collected by :term:`Percona Agent`.

.. glossary::

   Percona Toolkit
    A collection of advanced command-line tools
    to perform a variety of MySQL and system tasks.
    The toolkit is used by :term:`Percona Agent`
    to generate :term:`System Info` reports.

   Performance Schema
    An alternative source of query data to
    the :term:`slow query log`.
    Performance Schema is available starting from MySQL 5.6,
    and is enabled by default starting from MySQL 5.6.6.
    Data is collected from the
    ``performance_schema.events_statements_summary_by_digest`` table,
    and is used by the :term:`Query Analytics` tool.

    For more information, see :ref:`perf-schema`.

   Query Analytics
    A tool used for analyzing the history of MySQL queries.
    Data is collected either using the :term:`slow query log <Slow query log>`
    or :term:`Performance Schema`.

    For more information, see the :doc:`QueryAnalytics` section.

   slow query log
    The default source of query data for :term:`Query Analytics`.
    Slow query log is available starting from MySQL 5.1,
    and provides a wealth of valuable data for deep analysis.

    A faster and more efficient way (but without as much data)
    is the :term:`Performance Schema`.

   System Info
    A tool for viewing the status and configuration
    of the server and MySQL instances.
    It uses tools from :term:`Percona Toolkit` to generate the report.

    For more information, see :ref:`sysinfo`.

   user
    Owner of the :term:`PCT Account`.
