
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

- Eventlog key
- Event sources
- Event categories
- Event identifiers 
- Message files
- Event log records
- Event data


## EventLog Key

![image](https://user-images.githubusercontent.com/72671239/221772366-010d0fe1-29b4-474a-876d-e786b76161fe.png)

Note that domain controllers record events in the Directory service and File Replication service logs and DNS servers record events in the DNS server.

The event logging service uses the information stored in the Eventlog registry key. The Eventlog key contains several subkeys, called logs. Each log contains information that the event logging service uses to locate resources when an application writes to and reads from the event log.

In the Windows Event Log service, each log is like a separate folder that contains specific types of events and system messages. The EventLog registry key has several subkeys that represent these logs, such as the Application, System, and Security logs.

When an application wants to log an event or system message, it uses the _Windows event logging APIs_ to write to a specific log. For example, if an error occurs in a Windows system component, it may be logged in the System log. If an application encounters an error, it may log an event in the Application log.

The event logging service uses the information in the registry subkeys to locate the appropriate log when an application writes to or reads from the event log. Each log has specific settings, such as the maximum size of the log, how to handle events when the log is full, and whether to archive the log.

By separating events and system messages into different logs, system administrators can more easily filter and manage the information in the logs. For example, they can focus on the events in the System log to troubleshoot hardware or system-related issues, or they can focus on the Application log to troubleshoot issues with specific applications.

The EventLog registry key is like a settings file that tells the Windows Event Log service how to log events and system messages. It has information about how big the logs can be, when to overwrite old events, and whether to archive old logs. This registry key is usually managed by system administrators and should not be changed by regular users because it can affect the stability and performance of the system.

```
HKEY_LOCAL_MACHINE               =>  hardware, software, and user settings on the computer.
   SYSTEM                        => operating system, system drivers, and other system components.
      CurrentControlSet          => current hardware and system configuration
         Services                => system services installed
            Eventlog             => configuration of the Windows Event Log service
               Application       => logs
               Security          => logs
               System            => logs
               CustomLog         => logs
               
```
This is a representation of the Windows Registry hierarchy. It shows the location of the `Eventlog` subkey under the `Services` subkey in the `CurrentControlSet` subkey of the `SYSTEM` subkey under `HKEY_LOCAL_MACHINE`.

1. `HKEY_LOCAL_MACHINE` is the top-level key in the Windows Registry, which contains information about hardware, software, and user settings on the computer.
2. `SYSTEM` is a subkey under` HKEY_LOCAL_MACHINE` that contains information about the operating system, system drivers, and other system components.
3. `CurrentControlSet` is a subkey under `SYSTEM` that contains information about the current hardware and system configuration.
4. `Services` is a subkey under `CurrentControlSet` that contains information about the system services installed on the computer.
5. `Eventlog` is a subkey under `Services` that contains information about the configuration of the Windows Event Log service, including the settings for each log.
6. `Application`, `Security`, `System`, and `CustomLog` are subkeys under `Eventlog` that represent the different logs that can be created by the Windows Event Log service, each with their own settings and events.

By navigating to this part of the Windows Registry, system administrators can view and modify the settings for the Windows Event Log service, including the settings for each log, such as the maximum log size, retention policy, and security settings. This can help them troubleshoot issues, monitor system activity, and manage the logs more effectively.

The Windows Registry is organized in a hierarchical structure with multiple levels of keys and subkeys. Here is the full hierarchy of the Windows Registry:
```
HKEY_CLASSES_ROOT (HKCR)
  .exe
  .dll
  AppID
  CLSID
  Interface
  TypeLib
  MIME
  Extensions
  
HKEY_CURRENT_USER (HKCU)
  Control Panel
  Desktop
  Environment
  Keyboard Layout
  Network
  Printers
  Software
  System
  Volatile Environment
  
HKEY_LOCAL_MACHINE (HKLM)
  BCDEdit
  Hardware
  SAM
  Security
  Software
  System
    ControlSet00x
      Enum
      Services
        Eventlog
          Application
          Security
          System
          CustomLog
          
HKEY_USERS (HKU)
  .DEFAULT
  S-1-5-xx
    Control Panel
    Environment
    Keyboard Layout
    Network
    Printers
    Software
    System
    Volatile Environment
    
HKEY_CURRENT_CONFIG (HKCC)
  Hardware Profiles
  Software
```
Each key in the registry hierarchy contains multiple subkeys and values, which hold configuration settings, preferences, and other system information. System administrators can modify these keys and values to customize the behavior and settings of the Windows operating system and the applications running on it.

-----------------------------

## Event Sources
