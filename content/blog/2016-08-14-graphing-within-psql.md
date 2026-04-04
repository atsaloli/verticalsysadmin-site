---
title: "Graphing within psql"
date: 2016-08-14
author: "Aleksey Tsalolikhin"
---

Demonstrates creating graphs from SQL query results directly within [psql](http://postgresguide.com/utilities/psql.html) using [gnuplot](http://www.gnuplot.info/), without leaving the interface. Originally discussed on [Hacker News](https://news.ycombinator.com/item?id=5215040).

**Client-side method (Ian Barwick):** Consolidates preparation steps into a psql script:

```
testdb=# set plot_query 'SELECT * FROM plot'
testdb=# i tmp/plot.psql
```

**Server-side method (Sergey Konoplev):** Creates a server-side function. With gnuplot on the database server:

```sql
select just_for_fun_graph('select ... from ...', 'My Graph', 78, 24, ...)
```

Both eliminate the need to export data to external graphing tools.
