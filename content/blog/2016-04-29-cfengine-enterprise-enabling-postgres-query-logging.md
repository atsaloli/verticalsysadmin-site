---
title: "CFEngine Enterprise: Enabling Postgres Query Logging"
date: 2016-04-29
---

Since the CFEngine Postgres database internals aren't widely documented, you can learn more about them by observing what queries the Mission Portal sends to the DB (e.g., to do things like get the count of hosts with health issues which powers the health indicator you see in the Mission Portal status bar).

Postgres has a configuration parameter `log_statement` which you can change from `none` to `all` to enable query logging (i.e., all queries will get logged to `/var/log/postgresql.log`) to learn what queries the Mission Portal sends to the database.

Let's check what the default is:

`myhost# grep -i 'log_statement =' /var/cfengine/state/pg/data/postgresql.conf #log_statement = 'none' # none, ddl, mod, all myhost#`

The built-in default is `none`. The Postgres folks have the line commented out; to change it, uncomment the line and set the value to `all` to enable query logging. Then connect to the Postgres database and reload the configuration:

`myhost# /var/cfengine/bin/psql -U cfpostgres cfdb psql (9.3.2) Type "help" for help.  cfdb=# SELECT pg_reload_conf();  ## pg_reload_conf  t (1 row)  cfdb=# q myhost#`

Go to the UI and perform an operation (i.e. run a report) and you'll see in `/var/cfengine/postgresql.log` the SQL commands that the Mission Portal PHP UI sends to the Postgres database.
