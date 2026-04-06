---
title: "Looking up Postgres table name by id"
date: 2016-10-24
categories: 
  - "postgres"
---

When working with \[TOAST\]\[1\] tables, I had the relid (relation or table id) of the parent table, and needed to get its name.

Here is how to perform the lookup. For example, if the relid is 19665:

`SELECT relid, relname FROM pg_catalog.pg_statio_user_tables WHERE relid = '19665';`
