---
description: "Learn more about: MsSna_TN3270Port Class"
title: "MsSna_TN3270Port Class2"
ms.custom: ""
ms.date: "12/12/2023"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: reference
---
# MsSna_TN3270Port Class
Describes a port with security properties.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_TN3270Port : MsSna_Config  
{  
   String Service;  
   sint32 Port;  
   String Comment;  
   sint16 Security;  
   boolean ClientCertVal;  
   boolean Default;  
   String Name;  
};  
```  
  
## Properties  
 **Service**  
 Data Type: **String**Qualifiers: <strong>Key, MAXLEN(20)</strong>Access Type: Read/Write  
  
 The TN service to which this LU belongs.  
  
 **Port**  
 Data Type: **sint32**Qualifiers: **Key, MINVALUE(1), MAXVALUE(0xffff)** Access Type: Read/Write  
  
 The port number.  
  
 **Comment**  
 Data Type: **String**Qualifiers: <strong>MAXLEN(25)</strong>Access Type: Read/Write  
  
 An option comment field.  
  
 **Security**  
 Data Type: **sint16**Access Type: Read/Write  
  
 The security level. The following table describes the possible values for **Security**.  
  
|Value|Description|  
|-----------|-----------------|  
|0|Unsecured|  
|1|Low|  
|2|Medium|  
|3|High|  
  
 **ClientCertVal**  
 Data Type: **Boolean**Access Type: Read/Write  
  
 **true** to indicate that the client ceritificate should be validated; otherwise, **false**.  
  
 **Default**  
 Data Type: **Boolean**Qualifiers: <strong>(TRUE)</strong>Access Type: Read-Only  
  
 **true** to indicate a default port; otherwise, **false**.  
  
 **Name**  
 Data Type: **String**Qualifiers: **Something**Access Type: Read/Write  
  
 Name of the port.  
  
## Requirements  
 **Platforms**: Windows Server 2022, Windows Server 2019, Windows Server 2016, Windows 11, and Windows 10  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)
