For the Windows operating systems, much of the functionality of the OS is provided by DLL. Additionally, when you run a program, much of the functionality of the program may be provided by DLLs. For example, some programs may contain many different modules, and each module of the program is contained and distributed in DLLs.

The use of DLLs helps promote modularization of code, code reuse, efficient memory usage, and reduced disk space. So, the OS and the programs load faster, run faster, and take less disk space on the computer.

When a program uses a DLL, an issue that is called dependency may cause the program not to run. When a program uses a DLL, a dependency is created. If another program overwrites and breaks this dependency, the original program may not successfully run.

_With the introduction of the .NET Framework, most dependency problems have been eliminated by using assemblies._

A DLL is a library that contains code and data that can be used by more than one program at the same time. For example, the Comdlg32 DLL performs common dialog box related functions. Each program can use the functionality that is contained in this DLL to implement an Open dialog box. 

Additionally, updates are easier to apply to each module without affecting other parts of the program. For example, you may have a payroll program, and the tax rates change each year. When these changes are isolated to a DLL, you can apply an update without needing to build or install the whole program again.

The following list describes some of the files that are implemented as DLLs:

1. ActiveX Controls (.ocx) files: An example is a calendar control that lets you select a date from a calendar.

2. Control Panel (.cpl) files: An example is an item that is located in Control Panel. Each item is a specialized DLL.

3. Device driver (.drv) files: An example is a printer driver that controls the printing to a printer.

When a program or a DLL uses a DLL function in another DLL, a dependency is created. The program is no longer self-contained, and the program may experience problems if the dependency is broken. For example, the program may not run if one of the following actions occurs:

- A dependent DLL is upgraded to a new version.
- A dependent DLL is fixed.
- A dependent DLL is overwritten with an earlier version.
- A dependent DLL is removed from the computer.

These actions are known as DLL conflicts. If backward compatibility is not enforced, the program may not successfully run.
