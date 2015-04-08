.. _metrics:

Metrics Monitor
===============

The **Metrics Monitor** module provides an in-depth overview of metrics
that are critical for your server.
Metrics are represented on charts to show change over time.
You can set up separate dashboards for charts related to performance,
availability, and other types of statistics.
Or you can have separate dashboards for different members in your team.

.. note::
   * Use the **Time Range** menu to select the period of time,
     for which you would like to view metrics.
   * Use the **Host** menu to select the host that you want to monitor.

In the **Dashboard** drop-down list, select an existing dashboard
or create a new dashboard.

Adding Charts
-------------

A dashboard can be configured to contain several charts for various metrics.
Although a chart can contain any number of metrics,
do not overload it, unless you need to compare several metrics.
Keep it simple and separate different types of metrics across charts.


To add a chart to a dashboard:

1. Click **Add chart**.
#. Enter a name for the chart and a description.
#. Click **Add new serie**.
#. Start typing the name of the metric and select the one you need
   from the drop-down list.

   .. note:: There are many metrics available,
      separated into types and subtypes using the forward slash (``/``).
      For example, metrics that begin with ``disk/`` or ``memory/``
      are related to the general hardware and OS performance,
      while metrics related to MySQL begin with ``mysql/`` and ``mysqlvar/``.

#. Enter a custom description if necessary.
#. Select the type of the chart and the statistical value to be used.

   .. note:: The type and value depends on the metric and your needs.
      For example, you may want to see a bar chart of the count for
      created MySQL threads, and a line chart of the 95 percentile for
      MySQL query execution time.

#. Click **OK** to add the serie.
#. If necessary, add more series of metrics to the chart.
#. Click **Save** to add the chart to the dashboard.

Metrics Reference
-----------------

TBD
