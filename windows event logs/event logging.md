
When an error occurs, the system administrator or support representative must determine what caused the error, attempt to recover any lost data, and prevent the error from recurring. It is helpful if applications, the operating system, and other system services record important events, such as low-memory conditions or excessive attempts to access a disk. 

The system administrator can then use the event log to help determine what conditions caused the error and identify the context in which it occurred. By periodically viewing the event log, the system administrator may be able to identify problems (such as a failing hard disk) before they cause damage.

---------------------------------

![image](https://user-images.githubusercontent.com/72671239/221662843-9e47f0cb-b843-44e2-bde5-14dc6302e166.png)

Because the logging functions are general purpose, you must decide what information is appropriate to log. Generally, you should log only information that could be useful in diagnosing a hardware or software problem. Event logging is not intended to be used as a tracing tool.

## Choosing Events to Log
The following are examples of cases in which event logging can be helpful:

1. Resource problems: Logging a Warning event when memory allocation fails can help indicate the cause of a low-memory situation.

2. Hardware problems. If a device driver encounters a disk controller time-out, a power failure in a parallel port, or a data error from a network or serial card, the _device driver_ can log information about these events to help the system administrator diagnose hardware problems.

3. Bad sectors. If a disk driver encounters a bad sector, it may be able to read from or write to the sector after retrying the operation, but the sector will go bad eventually. If the disk driver can proceed, it should **log a Warning event**; otherwise, it should **log an Error event.** If a file system driver finds a large number of bad sectors and fixes them, logging Warning events might help an administrator determine that the disk may be about to fail.

4. Information events. A server application (such as a database server) records a user logging on, opening a database, or starting a file transfer. The server can also log other events such as errors (cannot access file, host process disconnected, and so on), database corruption, or whether a file transfer was successful.

---------------------------------------

Event logging consumes resources such as disk space and processor time. The amount of disk space that an event log requires and the overhead for an application that logs events depend on how much information you choose to log. This is why it is important to log only essential information. It is also good to place event logging calls in an error path in the code rather than in the main code path, which would reduce performance.

The amount of disk space required for each event log record includes the members of the EVENTLOGRECORD structure. This is a variable length structure; strings and binary data are stored following the structure.

--------------------------------

The following are the major elements used in event logging:

Eventlog key
Event sources
Event categories
Event identifiers
Message files
Event log records
Event data
