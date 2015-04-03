.. cloud-tools documentation master file, created by
   sphinx-quickstart on Tue Sep  2 11:45:14 2014.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

.. highlight:: bash

Welcome to Percona Cloud Tools Documentation!
=============================================

Percona Cloud Tools (PCT) is a cloud-based monitoring service for MySQL servers.
It provides valuable insight into your database and applications
that rely on MySQL performance.

Data is collected using Percona Agent,
which runs on a Linux server as a background service.
The agent sends MySQL metrics data to Percona Cloud through a secure connection,
where it is processed and stored.
You can access and analyse collected performance data using Percona Console,
which is a web interface accessed from your browser via HTTPS.

(ILLUSTRATION)

::

 -------------- PERCONA CLOUD TOOLS ----------------
 
 Percona Agent <=> Percona Cloud <=> Percona Console
        |                                   |
    Linux OS                                | HTTPS
        |                                   |
      MySQL                              Browser

Quick Start
-----------

To start using PCT:

1. Go to `cloud.percona.com <https://cloud.percona.com>`_,
   create a :term:`PCT Account` and log in.
#. Get your API key at
   `cloud.percona.com/api-key <https://cloud.percona.com/api-key>`_.
#. Install :term:`Percona Agent` by running the following command as root:

   ::

   $ curl -s https://cloud.percona.com/install | bash /dev/stdin -api-key="<API key>"

Contents
--------

.. toctree::
   :maxdepth: 1
   :includehidden:

   Account
   Agent
   WebInterface
   Performance
   MetricsMonitor
   QueryAnalytics
   Configuration
   PerfSchema
   Faq
   glossary

Help and Support
----------------

* If you're a Percona Support customer, get help through the
  `Percona Customer Portal <https://customers.percona.com/>`_.

* For bugs, please create an issue at https://jira.percona.com.

* For everything else, please ask, share, and help others on the
  `Percona Cloud Tools Community Forum <http://www.percona.com/forums/questions-discussions/percona-cloud-tools>`_.
