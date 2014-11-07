.. _performance:

Performance
###########

**Performance** dashboard provides nicely formatted information for all your servers in one place. Like the dashboard of a car, this data is vital but minimal. It's useful when everything should be ok and you're just taking a quick look to make sure that nothing has hit a wall.

.. image:: images/performance_dashboard.png

Performance dashboard provides the following information:

 * Last report - When was the last report received
  
 * Reported - Total size of reports received by *Percona Cloud Tools*
    
 * QPS - The number of queries per second that the server was executing

 * Total time - The total time of all executed queries

 * Load - Server load

 * Response 95% - Shows the response time in most of the cases (this means that users will get this response time in 95% of the cases).

Dashboard provides the quick links to the :ref:`query-analytics` and *metrics* for each server.

Reporting interval for the dashboards can be configured by selecting the predefined time periods or by creating your own by selecting the calendar icon.

.. image:: images/selector.png