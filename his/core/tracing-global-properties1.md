---
description: "Learn more about: Tracing Global Properties"
title: "Tracing Global Properties1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
f1_keywords: 
  - "trace_tracing_global_properties_tab"
---
# Tracing Global Properties
The **Tracing Global Properties** tab has several items that can be modified to adjust how Trace runs. These items include:  
  
## Trace File Flip Length  
 The default size is 20,000,000 bytes.  
  
 You can change the maximum length by highlighting the number and typing a new value.  
  
#### Tracing Global Properties tab to set the length of the trace file  
  
1.  In the **Trace Settings** dialog box, click the **Tracing Global Properties** tab.  
  
2.  Enter a value for the **Trace File Flip Length** box, and then click **OK**.  
  
## Allow HIS Administrators to perform tracing  
 Access to the HIS traces directory is controlled by security group. By default, Local Administrators have full control over the HIS traces folder. Also, by default, HIS Runtime Users have read/write access.  
  
 Select the **Allow HIS Administrators to perform tracing** option, to provide Full Control over the HIS traces folder to members of the HIS Administrators group.  
  
## Stop tracing by event  
 SNA Trace can monitor the Windows Event log and stop tracing when a configured event occurs. To enable this feature, click **Monitor event log** and enter an Event ID.  
  
## Write Traces on a Background Thread  
 Check this box to run tracing in the background. If the box is cleared (blank), tracing runs in the foreground.  
  
 To reduce performance impacts caused by tracing [!INCLUDE[hisHostIntegrationServerProduct](../includes/hishostintegrationserverproduct-md.md)] components, traces can be queued and written by a background thread when this box is checked. Otherwise, trace files will be written immediately.  
  
## Background Thread Priority  
 If you select **Write Traces on a Background Thread**, check only one item to set the level of priority for tracing to run within the Microsoft Windows operating system. Highest gives tracing the highest level of priority, which means that tracing takes precedence over other jobs. Idle means that tracing runs when the CPU is idle.  
  
## See Also  
 [SNA Trace Utility Fundamentals](../core/sna-trace-utility-fundamentals1.md)
