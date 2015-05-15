.. cloud-tools documentation master file, created by
   sphinx-quickstart on Tue Sep  2 11:45:14 2014.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

.. |PCT| replace:: :abbr:`PCT (Percona Cloud Tools)`

Welcome to Percona Cloud Tools Documentation!
=============================================

|PCT| is a cloud-based monitoring service for MySQL servers.
It provides valuable insight into your database and applications
that rely on MySQL performance.

Data is collected using a :term:`Percona Agent`,
which runs on a Linux server as a background service.
The agent connects to an API server
hosted by Percona through a secure websocket,
and stores MySQL metrics and other performance data in a database.
You can access and analyse collected performance data
using the web interface accessed from your browser via
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

.. note:: The following limitations apply for |PCT| beta:

  * Maximum 3 organizations per user
  * Maximum 5 agents per organization
  * Maximum 8 days of data per agent

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
