---
title: "Infrastructure Management at Scale"
date: 2016-07-26
---

I recently spoke at [Digital Media Educators Conference](http://ict-dm.net/faculty-pd/dmec) (DMEC) on Infrastructure Management at Scale and the skills educators need to impart to up and coming system administrators.

This conference serves the California community college system, which is dear to my heart. My mother worked at [West Los Angeles College](http://www.wlac.edu/) library her entire professional life in America, since we arrived in 1988. I used to volunteer and help her out with shelving in the summer. I was a very poor helper since I kept getting distracted by all the delicous books and did more reading than shelving.

While in high school I took computer programming, math and English at West Los Angeles College and at Santa Monica Community College, at first during summer break and then concurrent with eleventh grade, which allowed me to go to University instead of going to 12th grade.

So I have a personal connection to the California community college system and I jumped at the chance to contribute a talk:

![Cover slide](https://verticalsysadmin.com/wp-content/uploads/2016/07/0-cover-1.png)

Because my presentation was in the [Data Representation](http://ict-dm.net/index.php?option=com_zoo&view=category&layout=category&Itemid=820) track, I focused on Inventory and Compliance Reporting so I could show off CFEngine's slick UI.

I started by laying out CFEngine's philosophic groundwork: - [Promise Theory](https://en.wikipedia.org/wiki/Promise_theory) and the advantages of voluntary cooperation and distributed work over the limitations of imposed direct control. - The advantages of pull over push (see "Push versus pull" in [Deconstructing the \`CAP theorem' for CM and DevOps](http://markburgess.org/blog_cap2.html) by the author of CFEngine for more on this), and - The [Dunbar numbers](https://en.wikipedia.org/wiki/Dunbar%27s_number) which constrain the quality and quantity of relationships sysadmins are able to have with their infrastructures. The rest of the talk demonstrated how the design of CFEngine uses Dunbar numbers to focus the information it presents.

![Dunbar numbers](https://verticalsysadmin.com/wp-content/uploads/2016/07/1b-dunbar-iomedica-org.png)

We also talked about [what computer system administration IS](https://lopsa.org/System-Admin-Careers), and what the challenges are and how we handle them.

Then I introduced the CFEngine dashboard:

![Dashboard 1](https://verticalsysadmin.com/wp-content/uploads/2016/07/dashboard_1.png)

I pointed out the header which holds the host count (2, including the hub itself) and the health indicator (OK); the graph of Changes made by CFEngine, the fact that both of our hosts have Software Updates available (1 alert triggered on 2 hosts), and that we have 100% compliance on promise compliance and system health (green check-marks).

The next slide, adding a third host (notice the hosts indicator up top), shows how the Alert for Software Updates changes to a 2/3 arc, as, right after adding the host, as at this point the hub knows 2 out of 3 hosts are missing software updates. Once the agent runs on the third host and the hub collects the report, the Alert will change back to a full circle with 3 out of 3 hosts are missing software updates.

![Dashboard 2](https://verticalsysadmin.com/wp-content/uploads/2016/07/dashboard_2_out_of_3_hosts_have_updates_available.png)

The next slide illustrates how CFEngine communicates the **severity** of the alert: critical issues are indicated in red, less severe in orange (amber for you Aussies), and mildest level is yellow. I induced a policy non-compliance situation on one of the three hosts (e.g., promised a file edit but prevented CFEngine from accessing the file by filling up the disk), so the Promise Compliance alert spans 1/3 of the circle (1 out of 3 hosts).

![Dashboard 3](https://verticalsysadmin.com/wp-content/uploads/2016/07/dashboard_3_policy_compliance_not_kept.png)

Notice also that if CFEngine is unable to collect reports from a host or if an agent stops running on a host, the health indicator at the top of the screen changes from OK to a red number indicating the number of issues:

![Dashboard health indicator](https://verticalsysadmin.com/wp-content/uploads/2016/07/dashboard_6_health_0.png)

You can see the number and type of issues:

![Dashboard health detail](https://verticalsysadmin.com/wp-content/uploads/2016/07/dashboard_7_health_1.png)

Notice that the Dunbar numbers are in play here: CFEngine tells you there are issues, and if you want more data, then you can have it. But it doesn't throw all the detail at you at once, that would be too much.

You can get more detail on which hosts are not reporting by selecting "Hosts not reporting" from the health indicator menu:

![Hosts not reporting](https://verticalsysadmin.com/wp-content/uploads/2016/07/dashboard_7_health_1.png)

You can then select a host in the list of hosts not reporting to see the info for that host (host detail).

![Health issues host list](https://verticalsysadmin.com/wp-content/uploads/2016/07/dashboard_8_health.png)

![Host detail](https://verticalsysadmin.com/wp-content/uploads/2016/07/hosts_tree.png)

That actually takes us to the "Hosts" tab.

The "Hosts" tab starts in the "all hosts" view, where you see the promise compliance summary for your infrastructure:

![All Hosts](https://verticalsysadmin.com/wp-content/uploads/2016/07/promise-compliance-1.png)

You can list the hosts that have less than 100% compliance:

![Non-compliant hosts](https://verticalsysadmin.com/wp-content/uploads/2016/07/promise-compliance-2.png)

You can see which promises were not kept on each host:

![Promises not kept by host](https://verticalsysadmin.com/wp-content/uploads/2016/07/promise-compliance-3.png)

And that takes us to the "Reports" tab. There are many reports available but let's take a look at the Inventory Report. It starts out with four basic columns but you can add more:

![Inventory 1 - Start with 4 columns](https://verticalsysadmin.com/wp-content/uploads/2016/07/timezone-0.png)

You can extend inventory collection by writing CFEngine promises, for example, here I've added inventory of the host's timezone:

![Inventory 2 - User Defined](https://verticalsysadmin.com/wp-content/uploads/2016/07/timezone-1.png)

Let's say our company policy says all hosts must be in the UTC timezone. But in reality we have this:

![Inventory 3 - Timezone Detail](https://verticalsysadmin.com/wp-content/uploads/2016/07/timezone-2.png)

You can sort the column contents by selecting the column heading, this groups the outliers and brings them into view:

![Inventory 4 - Sort](https://verticalsysadmin.com/wp-content/uploads/2016/07/timezone-3-sorted.png)

You can graphically summarize column contents by selecting "Chart Data":

![Inventory 5 - Summary Chart Dialog](https://verticalsysadmin.com/wp-content/uploads/2016/07/timezone-4-chart-data-dialog.png)

Voila!

![Inventory 6 - Summary Chart](https://verticalsysadmin.com/wp-content/uploads/2016/07/timezone-5-pie-chart.png)

Hover over a slice to get more detail:

![Inventory 7 - Chart detail](https://verticalsysadmin.com/wp-content/uploads/2016/07/timezone-6-percentages.png)

Or switch to column view:

![Inventory 8 - Column View](https://verticalsysadmin.com/wp-content/uploads/2016/07/timezone-7-bar-graph.png)

Here is another example:

![Inventory 9 - AD status](https://verticalsysadmin.com/wp-content/uploads/2016/07/timezone-8-ad-status.png)

The charts can be exported and embedded in reports to management, auditors, etc.

Want to give CFEngine Enterprise a try? It's very easy to [download](https://cfengine.com/product/free-download/) and install the hub package.

Feel free to email me if you have any questions!
