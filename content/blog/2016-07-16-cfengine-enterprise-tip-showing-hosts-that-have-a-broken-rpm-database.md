---
title: "CFEngine Enterprise tip: showing hosts that have a broken RPM database"
date: 2016-07-16
---

RPM database corruption is a common problem on Red Hat Linux systems at scale.

When it happens, you have to rebuild the RPM database: - https://access.redhat.com/solutions/6903 - http://www.cyberciti.biz/tips/rebuilding-corrupted-rpm-database.html

I am working on automating this repair with CFEngine. In the meantime, here is a Custom Report to identify these systems:

```
-- Aleksey Tsalolikhin, 12 July 2016
-- Show hosts that have broken RPM databases

select hosts.hostname,changetimestamp
from promiseexecutions
inner join hosts on promiseexecutions.hostkey = hosts.hostkey
where logmessages::text ilike '%rpm%db3%' 
and changetimestamp >  current_timestamp - '24 hours'::interval
order by changetimestamp;
```
