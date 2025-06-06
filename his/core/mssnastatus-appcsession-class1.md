---
description: "Learn more about: MsSnaStatus_AppcSession Class"
title: "MsSnaStatus_AppcSession Class1"
ms.custom: ""
ms.date: "12/12/2023"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: reference
---
# MsSnaStatus_AppcSession Class
The **MsSnaStatus_AppcSession** class represents an APPC session status.  
  
## Syntax  
  
```  
  
class MsSnaStatus_AppcSession : MsSnaStatus_Config  
{  
   string APPCLU;  
   string SessionID;  
   string PartnerLU;  
   string Mode;  
};  
```  
  
## Properties  
 **APPCLU**  
 Data Type: **String** Qualifiers: **Key** Access Type: Read-Only  
  
 The Local APPC LU.  
  
 **SessionID**  
 Data Type: **String** Access Type: Read-Only  
  
 A unique ID for this session.  
  
 **PartnerLU**  
 Data Type: **String** Access Type: Read-Only  
  
 The Partner LU alias. **PartnerLU** can be a Remote LU or another Local LU.  
  
 **Mode**  
 Data Type: **String** Access Type: Read-Only  
  
 The mode name for this session.  
  
## Methods  
  
|Method|Description|  
|------------|-----------------|  
|GetObject|Retrieves the instance.|  
|EnumerateInstances|Enumerates all instances of the object.|  
|ExecMethod|Executes the specified method.|  
|[Stop](../core/mssnastatus-appcsession-stop-method1.md)|Stops the session.|  
  
 For more information on **GetObject**, **EnumerateInstances**, and **ExecMethod**, see [IWbemServices interface](/windows/win32/wmisdk/iwbemservices-methods).  
  
## Requirements  
 **Platforms**: Windows Server 2022, Windows Server 2019, Windows Server 2016, Windows 11, and Windows 10  
  
## See Also  
 [WmiSnaStatus WMI Provider Classes](../core/wmisnastatus-wmi-provider-classes1.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)
