---
description: "Learn more about: Code Page Mappings"
title: "Code Page Mappings"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Code Page Mappings
You can specify service-level and application-level code page mapping overrides. Also, you can specify code point mapping overrides within a defined code page. For more information, see Deployment.

## Troubleshooting Tools

### SQL Server tracing using Profiler
 SQL Server Profiler is a graphical user interface to SQL Trace for monitoring an instance of the Database Engine or Analysis Services. You can capture and save data about each event to a file or table to analyze later. For more information, see [Introducing SQL Server Profiler](/previous-versions/sql/sql-server-2008-r2/ms181091(v=sql.105)) (https://go.microsoft.com/fwlink/?LinkID=180433).

### DB2 provider tracing using HIS Trace Utility
 The Provider Trace Utility captures and saves information from the Microsoft client for DB2 network connections, OLE DB interfaces and data messages. For more information, see the Host Integration Server 2009 [Trace Utility Help](https://go.microsoft.com/fwlink/?LinkID=180447) (https://go.microsoft.com/fwlink/?LinkID=180447) and [SNA Trace Utility](https://go.microsoft.com/fwlink/?LinkID=180449) (https://go.microsoft.com/fwlink/?LinkID=180449).

### Network tracing using Network Monitor
 The Network Monitor captures network traffic for display and analysis. It enables you to perform tasks such as analyzing previously captured data in user-defined methods, extracting data from defined protocol parsers. It includes a Distributed Data Management (DDM) parser for use with the Data Provider. Contact Microsoft Customer Support Services for a copy of the DDM parser. For more information, see [Network Monitor](/windows/win32/netmon2/network-monitor) (https://go.microsoft.com/fwlink/?LinkID=180448).

### DB2 server tracing using IBM tools
 For more information, see the IBM DB2 Administration Guide for the applicable DB2 platform and version.

### Windows Server events using Event Viewer
 Enterprise Single Sign-On utilizes the Windows Application event log. The Event Viewer is a Microsoft Management Console (MMC) snap-in that enables you to browse and manage event logs. For more information, see [Event Viewer](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc766042(v=ws.11)) (https://go.microsoft.com/fwlink/?LinkID=131274).

### Event Tracing for Windows using Performance Monitor
 The DRDA Service ETW (Event Tracing for Windows) trace listener operates as an ETW provider to output trace data to a Windows ETW controller for access by ETW consumers. The Windows Performance Monitor uses performance counters, event trace data, and configuration information, which can be combined into Data Collector Sets. For more information, see [Performance Monitor](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc749249(v=ws.11)) (https://technet.microsoft.com/library/cc749249.aspx).

#### Start Event Trace Session
 The Windows administrator must start a DRDA Service ETW event trace session using Performance Monitor or the logman command line utility.

1. On the **Start** menu, point to **All Programs**, point to **Microsoft Visual Studio**, point to **Visual Studio Tools**, right **click Visual Studio x64 Win64 Command Prompt**, and click **Run as administrator**. The **User Account Control** dialog may appear. Click **Yes** to continue.

2. In the **Visual Studio x64 Win64 Command Prompt** window, locate the installation folder in which you downloaded the installation program, **logman start MsDrdaService -p {3B4388CE-50E0-404C-A62B-E9C87D4F3BC4} -o c:\temp\MsDrdaServiceETW.etl -ets**, and then click **Enter**.

   ```
   C:\Program Files (x86)\Microsoft Visual Studio 10.0\VC>logman start MsDrdaService -p {3B4388CE-50E0-404C-A62B-E9C87D4F3BC4} -o c:\temp\MsDrdaServiceETW.etl -ets
   The command completed successfully.
   ```

    <em>**Example 1.</em>* Start ETW event trace session command line argument with example property values.*

#### Stop Event Trace Session
 The Windows administrator can stop a DRDA Service ETW event trace session using Performance Monitor or the logman command line utility.

1. On the **Start** menu, point to **All Programs**, point to **Microsoft Visual Studio**, point to **Visual Studio Tools**, right click **Visual Studio x64 Win64 Command Prompt**, and click **Run as administrator**. The **User Account Control dialog** may appear. Click **Yes** to continue.

2. In the **Visual Studio x64 Win64 Command Prompt** window, locate the installation folder in which you downloaded the installation program, **logman stop MsDrdaService -ets**, and then click **Enter**.

   ```
   C:\Program Files (x86)\Microsoft Visual Studio 10.0\VC>logman stop MsDrdaService -ets
   The command completed successfully.
   ```

    <em>**Example 2.</em>* Stop ETW event trace session command line argument with example property values.*

#### Format Event Trace Session Data
 The Windows administrator can format DRDA Service ETW event trace session data using [Service Trace Viewer Tool (SvcTraceViewer.exe)](/dotnet/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe) or the tracerpt command line utility.

1. On the **Start** menu, point to **All Programs**, point to **Microsoft Visual Studio**, point to **Visual Studio Tools**, right click **Visual Studio x64 Win64 Command Prompt**, and click **Run as administrator**. The **User Account Control dialog** may appear. Click **Yes** to continue.

2. In the **Visual Studio x64 Win64 Command Prompt** window, locate the installation folder in which you downloaded the installation program, **tracerpt c:\temp\MsDrdaServiceETW.etl**, and then click **Enter**.

   ```
   C:\temp>tracerpt c:\temp\MsDrdaServiceETW.etl
   Input
   ----------------
   File(s):
        c:\temp\MsDrdaServiceETW.etl
   100.00%
   Output
   ----------------
   DumpFile:           dumpfile.xml
   Summary:            summary.txt
   The command completed successfully.

   ```

    <em>**Example 3.</em>* Format ETW event trace session data command line argument with example property values.*
