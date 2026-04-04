---
title: "CFEngine Enterprise: Enabling Postgres Query Logging"
date: 2016-04-29
author: "Aleksey Tsalolikhin"
---

"CFEngine Postgres database internals aren't widely documented." Enabling query logging reveals what SQL commands the Mission Portal sends to the database.

## Steps

1. Check /var/cfengine/state/pg/data/postgresql.conf for the log_statement parameter (default: none)
2. Uncomment and change to log_statement = all
3. Reload config: SELECT pg_reload_conf(); in psql
4. Perform operations in Mission Portal UI
5. Review logs in /var/cfengine/postgresql.log
