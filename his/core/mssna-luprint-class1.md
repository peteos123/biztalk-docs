---
description: "Learn more about: MsSna_LuPrint Class"
title: "MsSna_LuPrint Class1"
ms.custom: ""
ms.date: "12/12/2023"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: reference
---
# MsSna_LuPrint Class
Describes a 3270 LU printer resource.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_LuPrint   : MsSna_Lu3270  
{  
   String AssociatedLU;  
};  
```  
  
## Properties  
 **AssociatedLU**  
 Data Type: **String**Qualifiers: <strong>MAXLEN(8)</strong>Access Type: Read/Write  
  
 The associated display LU.  
  
## Remarks  
 **MsSna_LuPrint** is used by Print session or by printer emulation.  
  
## Requirements  
 **Platforms**: Windows Server 2022, Windows Server 2019, Windows Server 2016, Windows 11, and Windows 10  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)
