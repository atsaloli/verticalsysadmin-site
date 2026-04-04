---
title: "Mario Obejas on \"a replacement for bash?\" and on writing production-grade code"
date: 2016-05-29
author: "Aleksey Tsalolikhin"
---

Mario Obejas (34 years of industry experience) responded to a LOPSA-tech mailing list discussion on bash alternatives.

**On bash replacement:** Bash will likely only be replaced by an improved iteration (as bash replaced sh, vim replaced vi). "Bash works well enough for a lot of production work." Any successor must leverage existing widely-held skill sets.

**Real-world example:** Managing satellite data traffic for NASA's VIIRS ground station with bash scripts capable of recovering from catastrophic three-day outages without data loss — until the 2013 government shutdown disrupted operations for 17 days.

**Programming philosophy:** Primary recommendation: "put some damn comments in the code, like you are talking to somebody years later."
