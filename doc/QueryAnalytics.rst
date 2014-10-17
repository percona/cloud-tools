.. _query-analytics:

Query Analytics
###############

About
*****

**Query Analyitics** enables DBAs and application developers to analyze MySQL queries over long periods of time and shines a spotlight on problems. Query Analytics helps you:

 * Be sure your queries (tasks) are performed as expected
 * Queries are executed within the time frame you need
 * If not, then you will be able to see which query (or several) are problematic and requires attention
 * Get detailed metrics for each query

Query Profile
*************

Query profile provides the general information about the queries executed on the server. Query profile will show you which queries takes the most time in the database, and information on how many queries execute, total time they took, average time per query and 95% response time.

Following information is available in the Query Profile:

 * Rank - The query's rank within the entire set of queries analyzed
 * Query - The distilled query
 * Query ID - The query's fingerprint
 * Queries - The number of times this query was executed
 * QPS - The number of queries per second that the server was executing
 * Load - The wall clock time the server is busy with queries
 * Load % - Percentage of the wall clock time the server is busy with queries
 * Total Time - The total time of all executed queries (for server), or total time of fingerprinted query (for specific query). Queries with the biggest Total time value are causing most of the server load.
 * Avg Time - The average time of query execution
 * 95% - The 95th percentile; 95% of the values are less than or equal to this value. Shows user experience in most of the cases.
 * Max Time -  The longest period of time for query to be executed. Shows the worst user experience.

You can sort these queries by load they were causing on server (SUM) or by the amount of time it took to server to run them (MAX).

[SUM/MAX PICTURE]

You can filter this information by the time period by selecting the predefined time periods or by creating your own by selecting the calendar icon. 

[SELECTOR PICTURE]

Queries can also be filtered by :ref:`query_tags` and :ref:`query_status`.

When you click on any of the queries in the list you'll  get more details in the Query Details section. Query details provide the additional information:

 * Query Metrics - This section provides the detailed query metrics for the selected query. Some of the provided metrics are: Query count, Query_time, Lock_time, Rows_sent, Rows_examined, Rows_affected, and Bytes_sent. 

[QUERY METRICS PICTURE]

 For each of the metrics Query Analytics provide the historic data. Each of the metrics can be sorted by: Percent, Total, Average, Minimum, Median, 95%, Maximum, and Stddev to provide the additional and

 * Query Plan - This section shows information about the query plan for the selected query. Information available is: Filesort, Filesort on disk, Full join, Full scan, Query cache hits, Temporary tables, Temporary tables on disk

[QUERY PLAN PICTURE]

 * Query Example - This section provides the real example of the selected query. 
 
[QUERY EXAMPLE PICTURE]


.. _query_status:

Query Review
============

Query Review gives you the right resources to efficiently review your application's most important database activities. This enable you to assess, categorize, and comment on each of your application's queries.
New, Reviewed, Needs Attention

When you review your application's queries, Percona Cloud Tools will keep track of queries that have been evaluated. All queries can be marked as ``New``,``Reviewed``, or ``Needs attention``. All the queries are marked as ``New`` by default. These three phrases will save you significant time and can help you more efficiently perform query analysis as a team. New filters in Percona Cloud Tools also allow you to quickly assess the performance of new queries introduced in your latest code deployment.

.. _query_tags:

Query Tags
==========

Query tags are a flexible way to allow your team to use your own language to categorize queries. There are many ways to use tags. One approach we recommend is to record which queries belong to different sub-systems of your application such as ``checkout`` or ``hotel-search``. This should help to connect the experiences of your application’s users to the underlying queries.

Comments
========

Comments enable you and your team to better collaborate on improving the performance of your application as a team. Anyone that is a part of your organization can read and create query comments.
 
