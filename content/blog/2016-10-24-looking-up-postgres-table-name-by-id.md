---
title: "Looking up Postgres Table Name by ID"
date: 2016-10-24
author: "Aleksey Tsalolikhin"
---

When working with TOAST tables in PostgreSQL, you sometimes need to identify a table by its relation ID rather than its name. SQL query:

```sql
SELECT relid, relname FROM pg_catalog.pg_statio_user_tables WHERE relid = '19665';
```

Queries PostgreSQL's system catalog using the relation ID to return the table name.
