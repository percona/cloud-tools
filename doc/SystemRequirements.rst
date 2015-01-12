.. _SystemRequirements:

System Requirements
###################

* Linux OS
* root access
* Outbound network access to ``*.percona.com``, ports 80 and 443
* *MySQL 5.1* or newer, any distribution (*Percona Server*, *MariaDB*, etc.)

MySQL monitor
*************
* Local or remote access to *MySQL*
* MySQL user account with ``PROCESS`` and ``USAGE`` privileges

Server monitor
**************
* ``/proc`` filesystem
* Agent running on server

:ref:`QueryAnalytics <Query Analytics>` for Slow Log
*****************************************************
* Agent and *MySQL* running on the same server
* *MySQL* user account with ``SUPER``, ``USAGE``, and ``SELECT`` privileges

Query Analytics for :ref:`qa_performance_schema <Performance Schema>`
**********************************************************************
* *MySQL* 5.6 or newer, any distribution, including *Amazon RDS*
* *MySQL* user account with ``SELECT``, ``UPDATE``, ``DELETE`` and ``DROP`` privileges on ``PERFORMANCE_SCHEMA``

Supported Platforms and Versions
********************************

* Any 32-bit (i386) or 64-bit (x86_64) Linux OS
* *MySQL* 5.1 through 5.6, any distribution
* *Amazon RDS* (only *MySQL* monitor and Query Analytics for :ref:`qa_performance_schema <Performance Schema`>)
