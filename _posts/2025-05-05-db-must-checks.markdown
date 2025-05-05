---
layout: post
comments: false
mathjax: false
title:  "Database must checks before we say queries are slow"
excerpt: "We can't build applications without databases. Databases are everywhere. Oftentimes, we run into database issues like slow running queries and high response times. Check if you are doing these (simple) things."
date:   2025-05-05 10:00:00
---

We can't (practically) build applications without databases. Databases are everywhere.
Oftentimes, we run into database issues like slow running queries, high response times, sometimes database crash.

While *understanding and optimizing slow queries queries* and *how databases internally work* is an expertise in itself, but before we state the database is slow or taking huge disk space, you can start by checking the following simple, yet effective things:

1. You have optimally normalized the database schema and referenced foreign keys properly
2. You have used column sizes as much required, for example, if `varchar(1)` is ok you don't use `varchar(1024)`; if `short` is ok, you don't use `int`
3. You have not written `select * ` in queries, you have at least one `where` clause in your query and they are paginated with `limit` and `offset` as (and where) required ⭐
4. You have identified the searchable columns (columns on which we will frequently use `where` clauses), and you have indexed them
5. You have also indexed the "sortable" (`order by`) and `group by` columns
6. You have provisioned infra for your database that has main memory 1.5-2x of size of all the indices combined (1.5-2x is a good starting point, throw a bunch of load on your database and understand what's optimal for you)
7. You have used Connection Pools
8. You are doing batch inserts wherever you can ⭐⭐
9. (If you run delete statements quite often) You are doing soft deletes, later bulk delete as a periodic housekeeping ⭐⭐
10. Most importantly, your application is not making calls to the database just because it can... You optimize for database calls and hit the database only when you have to, and fetch just as musch data required


⭐ You would perhaps never require to run a `select` query that fetches all the data from the table; ideally never. If you think you need it, re-analyse your requirements. Sometimes it's important to simplify the problem instead of simplifying the solution.

⭐⭐ Every time we run an `insert` or a `delete` query, right after the `commit` the database re-adjust the indices.
For bulk inserts, the database will re-adjust the indices after the bulk insert, instead of re-adjusting them after every `insert`.
Same for `delete`. Soft delete is done by updating a column like `is_deleted` to `false` and capturing a time stamp. So this is an `update` rather than a `delete`.
Then you can have something as simple as a cron job (that may run during low traffic hours), to periodically bulk delete such soft deleted records at least seven days old.
You get the same advantage like you get during bulk inserts as explained above.

ORMs optimize database hits with bulk operations.

You can do it with raw SQL also, as a software engineer, this is one of the things you optimize for, that shows your maturity.

Another tip, for example in Postgres, use `explain` to understand how the query is executed. This is your first step to identify why a certain query is slow.
