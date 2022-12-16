Postmortem Report

<p align="center">
<img src="https://raw.githubusercontent.com/OliyadKebede/alx-system_engineering-devops/main/0x19-postmortem/report_cover_picture.PNG" width=100% height=100% />
</p>

# GitHub services were affected on October 22  post-incident analysis

### Summary

GitHub had a problem last week that caused the service to be down for 24 hours and 11 minutes. While certain parts of our platform were not impacted by this incident,
several internal systems were, which led to the display of outdated and conflicting information. No user data was ultimately lost, however manual reconciliation for a
brief period of database writes is still ongoing. Additionally, throughout the majority of the incident, GitHub was unable to create and publish GitHub Pages sites or
provide webhook events.


## Incident Timeline
**2018 October 21 22:52 UTC** - Because the database clusters in the US East and West Coast data centers now contained writes that were not present in the other data center, we were unable to fail the primary back over to the US East Coast data center safely.

**2018 October 21 22:54 UTC** - By this point the responding team decided to manually lock our internal deployment tooling to prevent any additional changes from being introduced.
**2018 October 21 23:13 UTC** - It was understood at this time that the problem affected multiple database clusters.

**2018 October 21 23:19 UTC** - We made an explicit choice to partially degrade site usability by pausing webhook delivery and GitHub Pages builds instead of jeopardizing data we had already received from users.

**2018 October 22 00:41 UTC** - A backup process for all affected MySQL clusters had been initiated by this time and engineers were monitoring progress.

**2018 October 22 06:51 UTC** -Our teams had identified ways to restore directly from the West Coast to overcome throughput restrictions caused by downloading from off-site storage and were increasingly confident that restoration was imminent, and the time left to establishing a healthy replication topology was dependent on how long it would take replication to catch up.

**2018 October 22 07:46 UTC** - We intended to send this communication out much sooner and will be ensuring we can publish updates in the future under these constraints

### Root Cause and Resolution
 During our recovery, we captured the MySQL binary logs containing the writes we took in our primary site that were not replicated to our West Coast site from
each affected cluster. The total number of writes that were not replicated to the West Coast was relatively small. For example, one of our busiest clusters had
954 writes in the affected window. We are currently performing an analysis on these logs and determining which writes can be automatically reconciled and which will
require outreach to users.

### Corrective and Preventive Measures
- Adjust the configuration of Orchestrator to prevent the promotion of database primaries across regional boundaries.
- While many portions of GitHub were available throughout the incident, we were only able to set our status to green, yellow, and red.
- tolerate the full failure of a single data center failure without user impact.
- We will take a more proactive stance in testing our assumptions.

### Conclusion
We know how much you rely on GitHub for your projects and businesses to succeed. No one is more passionate about the availability of our services and the 
correctness of your data. We will continue to analyze this event for opportunities to serve you better and earn the trust you place in us.
