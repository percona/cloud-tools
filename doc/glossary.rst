.. _glossary:

Glossary of Terms
=================

This is a glossary of terms related to Percona Cloud Tools (PCT).

.. glossary::

   API key
    A unique key used by :term:`Percona Agent` to identify the data it collects
    as belonging to the corresponding :term:`organization`.
    If you have a :term:`PCT Account`, you can find the API key at
    https://cloud.percona.com/api-key

    .. note:: Make sure that the correct organization is selected.

   Metrics Monitor
    A module of PCT for presenting collected MySQL and system metrics
    on time-based charts.

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
    An user account on `cloud.percona.com <https://cloud.percona.com>`_.

   Percona Agent
    A service that runs on the server,
    collects data about perfomance and MySQL metrics,
    and sends it to :term:`Percona Cloud`.

   Percona Cloud
    Internal infrastructure at the heart of PCT, hosted by Percona.
    In simple terms, it consists of an API server and a database server.
    The API is built to enable both :term:`Percona Agent`
    and :term:`Percona Console` to interact with the database
    of collected metrics.

   Percona Console
    Web-based graphical user interface (web GUI)
    that enables users to access data collected by :term:`Percona Agent`.

   Percona Toolkit
    A collection of advanced command-line tools
    to perform a variety of MySQL and system tasks.
    The toolkit is used by :term:`Percona Agent`
    to generate :term:`System Info` reports.

   Performance Schema
    TBD

   Query Analytics
    A module of PCT for analyzing the history of MySQL queries.

   Slow query log
    TBD

   System Info
    A module of PCT for viewing the status and configuration
    of the server and MySQL instances.
    It uses tools from :term:`Percona Toolkit` to generate the report.

   user
    Owner of the :term:`PCT Account`.
