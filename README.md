# Approach-to-Agile
These are my answers to a set of screening questions that I worked on. It gives an insight on how I approach Agile and Technology.

## **Q - You have been part of the team for 6 months, every sprint story has been slipping by 10-20% completeness, what could you suggest are possible causes of this?**

Is the team motivated enough? The pillars of motivation are:

- **Mastery** : people want to get better at what they do. Are they given the opportunity to sharpen their tools and learn new technologies/techniques?
- **Autonomy** : Do the team members feel trusted and empowered?
- **Purpose** : People work better if they feel that their job has meaning. Maybe the team can be reminded of the importance of their work and the positive impact it has in the company and outside of it.

As discussed in the book &quot;Scrum&quot; by Jeff Sutherland, **the cost of being interrupted in often underestimated**.

_&quot;Researchers at the University of California, Irvine, found after careful observation that the typical office worker is interrupted or switches tasks, on average, every three minutes and five seconds. And it can take 23 minutes and 15 seconds just to get back to where they left off.&quot;_

[https://www.washingtonpost.com/news/inspired-life/wp/2015/06/01/interruptions-at-work-can-cost-you-up-to-6-hours-a-day-heres-how-to-avoid-them/](https://www.washingtonpost.com/news/inspired-life/wp/2015/06/01/interruptions-at-work-can-cost-you-up-to-6-hours-a-day-heres-how-to-avoid-them/)

It is possible that team members are interrupted often by BAU issues or by people outside of the team for questions. One solution is to rotate that responsibility amongst team members. For instance, a team member can be on &#39;maintenance&#39; for a week. That person takes the call and emails for the team, debug any production issue, or reply to any Story sizing requests. That way, the other team members can focus on their Stories.

Also, the team may have too many meetings, and have its time scattered in too many places. Maybe the person on BAU and the Scrum Master can attend these meetings.

Another solution can be to put in place &quot;Interruption free time&quot;, where the team members can focus on their work. For instance, people could be asked to interrupt the team only in the morning, so the team can focus on their work in the afternoon.

It is possible that production issues are difficult to troubleshoot because of a lack of proper error logging systems. Tools like Raygun or New Relic are great at identifying issues quickly.

Upgrading the systems can take too much time. The deployment process can be automated for instance, using tools like Octopus Deploy, instead of having to update the servers manually. Also, **Regression Tests** may take too much time between sprints. Automating regression tests can save a lot of time, using **Selenium** for instance.

Is the team facing a recurring external impediment? Maybe a vendor is causing troubles, or a third party is going down often. The **Sprint Retrospective** is a good time to mention any blockers and any impediments that causes problems.

Maybe the stories are not sized correctly. Is the team using **Story Points** instead of days during the Sprint Planning? A story point is like a currency, its value can change over time, depending on several factors: has the team new members, new methodologies, new impediments... Story Points can then help calculating the **Velocity** of the team and each team member.

Has the team a **Definition of Done**? Maybe it hasn&#39;t, so factors like the time to QA or the time for Unit tests is left off during the Sprint Planning, and result as overheads during the Sprint.

Maybe the team has faced a spike of work and cannot recover from it. It is possible to hire contractors to offload some of the work if the workload gets unusually high, or to hire remote workers for repetitive tasks like regression tests for instance.

Running the unit tests, code reviews, deployments, regression tests, notifications can all be automated in a **Continuous Delivery pipeline** using TeamCity or Bamboo.

**A real life example** : as the Scrum Master of the internal Digital Agency of Ninemsn, we encountered a spike of work as more and more contracts kept coming in. The deadlines were short, and the clients very demanding. The solution was to hire a couple of contractors during that period, and to reduce the number of meetings that the team had to go to to free up some time in their calendar. Finally, I was made the principal point of contact for any queries, so the team could focus on their work. The projects were delivered on time.


## **Q - What would you do if you notice that coding standards and re-use aren&#39;t as good as they could be? Can you introduce an iterative process suggesting how this could be improved?**

**Pair-programming** can help improving the coding quality, as software engineers can discuss their views about their proposed solutions and bring their shared knowledge of the code base.

Tools like Resharper (by JetBrains), CodeRush (by DevExpress) or JustCode (by Telerik) can give **code reviews on the spot** as it will highlight any syntax problems or give hints and shortcuts to achieve the same result with less code.

**Code reviews can be automated** using tools like SonarQube. This way, each developer can know straight away after a commit if his/her code is causing any issues.

**Code reviews** by colleagues are also a great tool of checking the quality of the code. Using tools like Stash, a Story/Branch can be reviewed and discussed by the technical leads and the other team members.

Technical leads and the team can work together on a **Documentation** tool like Confluence to give guidelines on how to implement a story, explain the layers of the project to newcomers and give a set of recommended of tools and techniques.

Also, coding standards can be discussed during the **Scrum Planning** and **Sprint Retrospective**. For instance, a difficult Story can be discussed with the whole team during the sprint planning so Senior members can give hints on how to develop the feature. And the technical details of a story can be discussed at the end of the Sprint, so the parts of the code that are reusable can be shown to the rest of the team.

Having each new story being Unit Tested can improve the quality of the code drastically. **Unit Tests** enforces most of the **SOLID principles** and using **Composition over Inheritance** , as discussed in the book &quot;Design Patterns&quot; by the Gang of Four. Unit Tests helps spotting any errors caused by edge cases.

Finally, a round of **Load Testing** helps finding any bottlenecks introduced in the application. Visual Studio allows creating load testing projects, and running them can be automated in the **Continuous Delivery pipeline**.

**A real life example** : While working at IAG, each developer had Resharper installed to get instant feedback, then the story was automatically reviewed in SonarQube after being pushed. After that, a peer would review the story in Stash, and finally the story was load tested by another team.


## **Q - The application we have been working on has recently been encountering a number of different error spikes with random downtime throughout the day. How would you approach the debugging process to identify the root cause?**

Does the issue follow a release? It can help knowing if the issues has been caused by a change in the code base, or if the issue is caused by an external factor.

If the issue follows a release and is a major problem, maybe it would be wiser to **roll back** the deployment in order to fix the problem offline in the Staging environment.

One way of troubleshooting an issue is to look at the logs, for instance those left by Raygun. It is also possible to remote desktop directly into the live machine and check the server&#39;s Event logs and its status: RAM Memory, hard drive, CPU...

Tools like Resharper dotTrace allows doing the equivalent of a debug session onto a remote server, and use the traces to spot any errors or bottlenecks. It logs any exception and the time taken by functions to execute.

[https://www.jetbrains.com/help/profiler/Starting\_Remote\_Profiling\_Session.html](https://www.jetbrains.com/help/profiler/Starting_Remote_Profiling_Session.html)

Does the system involve third parties? Maybe the API of a vendor is down, we may need to check that all the systems that the application is connecting to are up.

It can happen also that a CDN provider is down, for instance the provider of the Twitter Bootstrap CDN may be unreachable. We may need to ping all the third parties to check their availability.

In Chrome, the console can help spotting any element that loads slowly, or any unusual error,

Finally, maybe the servers that the application is hosted on are having issues.

If the application is hosted in the cloud, we can contact the provider to see if they have encountered any issues on their side.

If the application is not hosted in the cloud, we can check that the physical machine is working properly. We can check that the fans are working and that the machine is not overheating, that it is well connected to the internet, and that it is not showing any errors while logging into it.

We can check also that the Internet Service Provider (ISP) hasn&#39;t encountered any issues.

**A real life example** : after a deployment of JobAdder, one of the script seemed not to be working properly. After investigation, it turned out that the automatic increment of version number for the refresh of the script cache didn&#39;t occur. It showed that a previous deployment at broken it. It was then fixed and the feature worked as intended.


## ** Q - What would you do if you noticed that databased responsiveness is down? What steps would you take to troubleshoot the issue?**

If I can remote desktop onto the server, I would open the **Performance Monitor** and check that the check hard drive or the RAM memory aren&#39;t full, that the CPU is not overloaded, and that the I/Os of the hard drive are not plateauing.

If the hard drive is full, maybe it would be useful to do some clean-up or **shrink** the database and clear up the logs. Also, an index or a table may be taking too much space, or it may be time to archive unused data.

The network may have some difficulties. The internet speed of the database server can be checked using a tool like [www.speedtest.net](http://www.speedtest.net).

The error logs can be checked. The location of the file can be found in **SQL Server Management Studio** or in **SQL Server Configuration Manager**.

It is possible that the connections to the database aren&#39;t pooled, which would mean that the database creates a new connection for each new query. The current users and transactions can be checked using &quot;sp\_who&quot; in MS SQL.

The increase of amount of data may have made some queries take longer to execute. Individual stored procedures execution time can be monitored to check that it hasn&#39;t blown out of proportion.

Also, it is possible to do some **live profiling** of the database using   **SQL Server Profiler** to see which queries are run the most and how much time they take.

It is possible that some queries are not well formed. After finding the queries that take the longest to execute during the profiling, we may find out that clustered and nonclustered indexes are missing, or that some SELECT are missing a (NOLOCK) statement to avoid deadlocks.

If it isn&#39;t possible to remote desktop into the database server, maybe the hardware has gone down. If the database is hosted in the cloud, we may need to contact the provider to check if they are having any issues on their side and if they can reboot the machine.

If the machine is not hosted in the cloud, we may need to check the physical machine. (see the answer of the previous question)

Also, **caching** is a great way of resolving a slow response time for long queries. The cache can be implemented at web server level, or at CDN level.

**A real life example** : while working at Ninemsn, some live statistic requests took too much time to execute if accessed by a large number of clients. The solution was to cache the results for one minute using Akamai. We never had any issues with these queries from then on.


## **Q - In mid-sprint, you have been asked to investigate a task/issue and you aren&#39;t entirely comfortable with all elements of the task. How would you approach this? If this happened during sprint planning would you speak up on the spot or would you prefer to troubleshoot yourself first?**

I believe that **good communication** is paramount in this context. My concerns would be brought up as soon as possible, but also at the right moment: during the stand-up for instance.

As said previously, the cost of interrupting a colleague can be high, so I would try to choose wisely when asking the opinion of somebody else, so they can focus on their own work.

I would first spend some time trying to solve the issue myself. Maybe the problem is already documented in the code base, or maybe in the company Wiki. Also, other users may have encountered that problem before, so having a look at a website like Stackoverflow may be a good idea.

Sometimes a Story may be too vague to work on, so I may ask the Scrum Master of the Product Owner for clarifications.

If I believe the Story may be difficult to tackle, I may bring this up during the **Sprint Planning** or the **Stand-Up** , so it is taken into account in the **Sprint Backlog**.

**A real life example** : While working at Virgin Mobile, I chatted with a colleague and realised that he was working on a feature that was changing the exact same code than the feature I was on. The issue was escalated to the Scrum Master and the Product owner, and we decided to merge the branches of the features and release them together.


## ** Q - In mid sprint the scrum master is away sick and cannot be contacted. You encounter a blocker regarding an external resource – what would you do?**

I would let the team know during the stand-up, maybe the Product Owner or the Project Manager are aware of this issue and know about how to resolve it.

If not, I would contact the provider itself to try to figure out how the issue can be addressed.

**A real life example** : While working at Betclic, the French leader of Online Sports Betting, we implemented a video player so the users could see the live match while betting on it. But during the development phase, one of the video providers kept on returning errors. After a lot of back and forth with their Austrian team, I figured out that they had turned on a security setting that prevented us connecting to their servers, and their sales team was not aware of it. The problem was fixed, the feature went live and worked as expected.
