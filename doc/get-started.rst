.. |PCT| replace:: :abbr:`PCT (Percona Cloud Tools)`

.. _get-started:

========================================
Getting Started with Percona Cloud Tools
========================================

|PCT| is a hosted service that helps you manage MySQL performance.
It provides insight into problematic queries and performance spikes
that you may not notice with other tools.

.. contents::
  :local:

How PCT Works
-------------

Data is collected using :term:`Percona Agent`:
a free, open-source, single-binary application.
You can install *Percona Agent* on any Linux server with one command.
The agent runs as a background service
and connects to |PCT|  through a secure websocket.
Collected MySQL metrics and other performance data is stored
where only you and members of your team can access it.
You can access the web application to analyse your data at
`cloud.percona.com <https://cloud.percona.com>`_
using any browser that supports
:abbr:`HTTPS (Hypertext Transfer Protocol Secure)`.

.. image:: images/pct-diagram.png
  :align: center

Tools
-----

|PCT| provides several tools for analysing collected data:

* :ref:`qan` aggregates query digest data to see which queries cause problems.
  You can see a range of metrics for each individual query
  and run diagnostic queries to see execution details.

* :ref:`mm` enables you to set up dashboards with charts
  to monitor trends in MySQL and general system performance.
  You can drill down into problematic periods
  and compare metrics to see dependencies
  that might uncover the cause of problems.

* :ref:`sys-info` provides a summary of information
  related to MySQL and system configuration.

* :ref:`reports` are a way to get critical query digest data
  delivered to you regularly.

Quick Start
-----------

If you have MySQL server running and configured correctly,
you can start using |PCT| in three easy steps:

1. **Create account**

  Go to `cloud.percona.com <https://cloud.percona.com>`_,
  create a :term:`PCT Account` and log in.

2. **Get your API key**

  Get your :term:`API key` at
  `cloud.percona.com/api-key <https://cloud.percona.com/api-key>`_.

3. **Install Percona Agent**

  Log in to your MySQL server as **root** and run the following command:

  ::

  $ curl -s https://cloud.percona.com/install | bash /dev/stdin -api-key="<API key>"

:download:`Check out this video to see how easy it is to get started
<files/getstarted.mp4>`

For more information about installing Percona Agent,
see the :ref:`Installation Guide <install>`.

Switching Organizations
-----------------------

When you register a PCT account, a default organization is created for you.
You can use this default organization if you are planning to use |PCT| alone.


Selecting Time Range
--------------------

Using the Instance Tree
-----------------------
