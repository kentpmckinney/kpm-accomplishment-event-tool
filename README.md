
# Event Log Reporting Tool

An event collection system optimized to reduce network utilization

<br/>

Company: Healthesystems


Year: 2013

Purpose: I was tasked with a project to deploy AppLocker to all company workstations, and part of the project was to devise a way to validate the effectiveness of AppLocker rules with a high degree of certainty and to resolve problems with rules before they affected users. I found that this could best be done by reviewing event log data, so we needed a way to collect that data for all workstations. After evaluating several choices, including SCCM, Lansweeper, Windows Event Collectors, and some third-party products, I opted to use PowerShell for three main reasons.

1. PowerShell Remoting could be used in most cases to run a script on the client side, which allows infinite possibility for tailoring data sent back to the server. By preventing unneeded events from being passed back to the server, CPU and memory utilization on the server was kept to a minimum and unnecessary data storage was avoided.
1. Network throughput was at a premium to branch locations, and minimizing data sent over the network was a requirement. For the same reasons it minimized server CPU, memory, and storage utilization, PowerShell also minimized network throughput, and it consumed far less traffic than any other option I looked at.
1. PowerShell made it easy to store data in SQL, and by doing so, greatly reducing the complexity of working with the data.

My Role: I was the technical lead for the project and I performed the work.

Outcome: Though the event collection data was used for other purposes as well, the primary use was to analyze AppLocker audit-mode data over a period of several months. This allowed for the creation of a number of rules to allow all approved software prior to the initial pilot. When AppLocker was finally rolled out, there were few surprises and the deployment went smoothly.

Technical Details: The non-GUI event collection scripts ran as scheduled tasks from a server. The scripts ran hourly, checking for systems that were on the network and collecting the events that had transpired since the last successful collection on each workstation. The collected data was uploaded to a SQL table. The GUI tool was written in PowerShell and compiled into an executable by PowerShell Studio. The GUI simply queries the SQL database to display relevant data.

### Previewing this Project
![](http://kentpmckinney.github.io/kpm-achievement-event-tool/EventLogReportingTool1.png)

<br/>

### Technologies Used

<code>PowerShell</code>
<br/>
<br/>

### Authors

[kentpmckinney](https://github.com/kentpmckinney)
<br/>
<br/>

###### <sub>Copyright&copy; 2020 [kentpmckinney](https://github.com/kentpmckinney). All rights reserved.</sub>