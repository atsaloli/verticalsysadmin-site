---
title: "CFEngine Enterprise Tip: Showing Hosts with Broken RPM Databases"
date: 2016-07-16
author: "Aleksey Tsalolikhin"
---

RPM database corruption is a common problem on Red Hat Linux at scale. Custom SQL query for CFEngine Enterprise to identify affected systems:

```sql
select hosts.hostname,changetimestamp
from promiseexecutions
inner join hosts on promiseexecutions.hostkey = hosts.hostkey
where logmessages::text ilike '%rpm%db3%' 
and changetimestamp > current_timestamp - '24 hours'::interval
order by changetimestamp;
```

Searches the past 24 hours of promise executions for log messages containing "rpm" and "db3", returning hostnames and timestamps.
