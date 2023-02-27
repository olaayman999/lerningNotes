Logs are records of events that happen on your computer, either by a person or by a running process. They help you track what happened and troubleshoot problems.

 Some applications also write to log files in text format. For example, IIS Access Logs.
 
Windows Event Viewer displays the Windows event logs. Use this application to view and navigate the logs, search and filter particular types of logs, export logs for analysis, and more. 


Description-critical event ids- parameters - explain id and important files- why is it important- usecases- map to mitre tactics


Event Log Categories:

1. Application Log

Any event logged by an application. These are determined by the developers while developing the application. Eg.: An error while starting an application gets recorded in Application Log.

2. System Log

Any event logged by the Operating System. Eg.: Failure to start a drive during startup is logged under System Logs

3. Security Log

Any event logged by the Operating System. Eg.: Failure to start a drive during startup is logged under System Logs

4. Custom Log

Custom Event Logs where you can categorize event records by their event source and store them in a separate event log. This can be useful if you would like to organize events by their source. In doing so, you are redirecting the log entries to an event log that you specify.

5. Directory Service log

records events of AD. This log is available only on domain controllers.

6. DNS Server log

records events for DNS servers and name resolutions. This log is available only for DNS servers


7. File replication service log	

records events of domain controller replication This log is available only on domain controllers.


Types of Event Logs:

1. Information	

An event that describes the successful operation of a task, such as an application, driver, or service. For example, an Information event is logged when a network driver loads successfully.

2. Warning

An event that is not necessarily significant, however, may indicate the possible occurrence of a future problem. For example, a Warning message is logged when disk space starts to run low.

3. Error

An event that indicates a significant problem such as loss of data or loss of functionality. For example, if a service fails to load during startup, an Error event is logged.

4. Success Audit (Security log)

An event that describes the successful completion of an audited security event. For example, a Success Audit event is logged when a user logs on to the computer.

5. Failure Audit (Security log)	

An event that describes an audited security event that did not complete successfully. For example, a Failure Audit may be logged when a user cannot access a network drive.


https://www.kaspersky.com/resource-center/definitions/replay-attack
