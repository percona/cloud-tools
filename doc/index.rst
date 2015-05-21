.. cloud-tools documentation master file, created by
   sphinx-quickstart on Tue Sep  2 11:45:14 2014.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

.. |PCT| replace:: :abbr:`PCT (Percona Cloud Tools)`

Welcome to Percona Cloud Tools Documentation!
=============================================

.. sidebar:: Beta

  |PCT| is currently in beta. The following limitations apply:

  * 3 organizations per user
  * 5 agents per organization
  * 8 days of data per agent

|PCT| is a cloud-based monitoring service for MySQL servers.
It provides valuable insight into your database and applications
that rely on MySQL performance.

.. contents::
  :local:

How PCT Works
-------------

Data is collected using :term:`Percona Agent`:
a free, open-source, single-binary application.
You can install *Percona Agent* on any Linux server with one command.
The agent runs as a background service
and connects to an API server hosted by Percona through a secure websocket.
Collected MySQL metrics and other performance data is stored
where only you and members of your team can access it.
You can access the web application to analyse your data at
`cloud.percona.com <https://cloud.percona.com>`_
using any browser that supports
:abbr:`HTTPS (Hypertext Transfer Protocol Secure)`.

.. image:: images/pct-diagram.png

Quick Start
-----------

To start using |PCT|:

1. Go to `cloud.percona.com <https://cloud.percona.com>`_,
   create a :term:`PCT Account` and log in.
#. Get your :term:`API key` at
   `cloud.percona.com/api-key <https://cloud.percona.com/api-key>`_.
#. Install *Percona Agent* by running the following command as root:

   ::

   $ curl -s https://cloud.percona.com/install | bash /dev/stdin -api-key="<API key>"

Contents
--------

.. toctree::
   :maxdepth: 1
   :hidden:

   Account
   Agent
   WebInterface
   Performance
   MetricsMonitor
   QueryAnalytics
   Configuration
   Faq
   glossary

:doc:`Account`
 How to create and manage your *PCT Account*.

:doc:`Agent`
 How to install, manage, update, and uninstall *Percona Agent*.

:doc:`WebInterface`
 Understanding the general layout of the web UI.

:doc:`Performance`
 How to get a quick overview of your infrastructure.

:doc:`MetricsMonitor`
 How to use the *Metrics Monitor* tool.

:doc:`QueryAnalytics`
 How to use the *Query Analytics* tool.

:doc:`Configuration`
 How to configure |PCT|.

Help and Support
----------------

* If you're a Percona Support customer, get help through the
  `Percona Customer Portal <https://customers.percona.com/>`_.

* For bugs, please create an issue at https://jira.percona.com.

* For everything else, please ask, share, and help others on the
  `Percona Cloud Tools Community Forum <http://wwcw.percona.com/forums/questions-discussions/percona-cloud-tools>`_.
