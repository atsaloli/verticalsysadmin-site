---
title: "Mario Obejas on \"a replacement for bash?\" and on writing production-grade code in any language."
date: 2016-05-29
---

Recently Yves Dorfsman asked on the [lopsa-tech](https://lists.lopsa.org/pipermail/tech/2016-May/017624.html) mailing list:

> A lot of people love to hate bash, and there are good reasons for it, but it seems that there isn't an obvious replacement for it. \[...\] What do **you** use? Do you see any clear winner to replace it on the horizon?

Mario Obejas, a popular occasional Instructor for Vertical Sysadmin, and living proof that there is [life after system administration](https://www.linkedin.com/in/mario-obejas-77b78a5), answered with this gem. This is the voice of 34 years of Software Development, Infrastructure, and Information Security experience, folks. (Thanks for allowing us to re-post it here, Mario!)

bash replaced sh the same way vim replaced vi, for many of the same reasons. They took what was working, kept the solid parts of the base and improved it. The jury is back - bash works well enough for a **lot** of production work.

My prediction, Yves, is that the only thing that will replace vim and bash to the same degree will similarly be another iteration that improves upon the already existing widely installed vim and bash base, and leverages the same widely held skill sets.

Some things, like a Ted Cruz, _no_ language can deal with. The last production bash scripts I wrote were to provide data traffic management between the VIIRS satellite ground station and NASA's net, through their itty bitty data pipe. Our requirements were to be able to recover from up to a catastrophic three day data clog or outage, without losing any of the satellite data. We did very well through 2013 until Ted affected us. Nobody expected a 17 day US government shutdown .....

I'm an odd data point with respect to languages. I loved PASCAL and ADA. But here's some heresy - I hate C. That's probably due to the way a lot of people write C, which I characterize as, "as obfuscated and comment free as possible". I think most people write C with speed in mind (filling in the diamond or checkbox on the schedule) versus maintainability (write like you will not see the code for a year, and then you will have to come back and upgrade/extend it).

We wrote Theater High Altitude Air Defense in Ada. When the day came to integrate our code (including that of our partners and contract vendors) in the lab, we were all shocked to find the system cycling, acquiring and tracking targets, not crashing as expected. We had to go back to our offices and retrieve the formal tests, nobody expected that level of robustness the first week, much less the first 15 minutes.

For longevity, my oldest production code is the Jovial and assembly I wrote for three Middle East mountaintop radars. I participated in the customer selloff in 1984, and 29 years later I received a call in December 2013 - no kidding - about helping the team to do an upgrade in 2014. It was still working(!). The only other longer lived code I know about is off world (satellites) or in the "Don't touch it!" holy COBOL shrines.

Tangential moral of the story: regardless of language, put some damn comments in the code, like you are talking to somebody years later and explaining what the code does. That somebody might be you, years later.
