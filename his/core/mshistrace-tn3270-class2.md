---
description: "Learn more about: MsHisTrace_TN3270 Class"
title: "MsHisTrace_TN3270 Class2"
ms.custom: ""
ms.date: "12/12/2023"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: reference
---
# MsHisTrace_TN3270 Class
The **MsHisTrace_TN3270** class contains tracing properties for the TN3270 service.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsHisTrace_TN3270 : MsHisTrace_Config  
{  
   string Name;  
   uint32 EnabledTraces;  
   Boolean InternalMessageTrace;  
   Boolean T3270Trace;  
   Boolean LU62Trace;  
   Boolean APPCTrace;  
   Boolean CPICTrace;  
   Boolean LUATrace;  
   Boolean CSVTrace;  
   Boolean TraceState;  
}  
```  
  
## Properties  
 **Name**  
 Data Type: **String** Qualifiers: **Key** Access Type: Read/Write  
  
 Name of the configuration file.  
  
 **EnabledTraces**  
 Data Type: **uint32** Access Type: Read/Write  
  
 Bitmap that indicates which Internal Trace conditions to record. The following table describes the possible values for **EnabledTraces**.  
  
|Value|Description|  
|-----------|-----------------|  
|1|Fatal trace mask|  
|2|Error trace mask|  
|4|Debug trace mask|  
|8|State trace mask|  
|16|Function trace mask|  
|32|Message trace mask|  
|64|Custom trace mask|  
|128|Plan enter exit mask|  
  
 **InternalMessageTrace**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to enable tracing of internal messages; otherwise, **false**.  
  
 **T3270Trace**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to enable T3270 tracing; otherwise, **false**.  
  
 **LU62Trace**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to enable LU 6.2 tracing; otherwise, **false**.  
  
 **APPCTrace**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to enable APPC tracing; otherwise, **false**.  
  
 **CPICTrace**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to enable CPI-C tracing; otherwise, **false**.  
  
 **LUATrace**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to enable LUA tracing; otherwise, **false**.  
  
 **CSVTrace**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to enable CSV tracing; otherwise, **false**.  
  
 **TraceState**  
 Data Type: **Boolean** Access Type: Read/Write  
  
 **true** to enable the TN3270 Internal Trace; otherwise, **false**.  
  
## Requirements  
 **Platforms**: Windows Server 2022, Windows Server 2019, Windows Server 2016, Windows 11, and Windows 10  
  
## See Also  
 [WmiSnaTrace WMI Provider Classes](../core/wmisnatrace-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)
