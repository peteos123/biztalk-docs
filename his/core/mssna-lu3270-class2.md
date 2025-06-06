---
description: "Learn more about: MsSna_Lu3270 Class"
title: "MsSna_Lu3270 Class2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: reference
---
# MsSna_Lu3270 Class
Describes the base class for a 3270 LU resource.  
  
 The following syntax is simplified from MOF code.  
  
## Syntax  
  
```  
  
class MsSna_Lu3270 : MsSna_Resource  
{  
   String Name;  
   String ConnectionName;  
   String Comment;  
   String PoolName;  
   sint16 Number;  
   boolean Compression;  
   boolean UserWksSecure;  
};  
```  
  
## Properties  
 **Name**  
 Data Type: **String**Qualifiers: **Key, MAXLEN(8), TOUPPERCASE**Access Type: Read-Only  
  
 The LU Name.  
  
 **ConnectionName**  
 Data Type: **String**Qualifiers: **MAXLEN(8), TOUPPERCASE**Access Type: Read/Write  
  
 The connection on which this LU is defined.  
  
 **Comment**  
 Data Type: **String**Qualifiers: <strong>MAXLEN(25)</strong>Access Type: Read/Write  
  
 An optional comment field.  
  
 **PoolName**  
 Data Type: **String**Qualifiers: <strong>MAXLEN(8)</strong>Access Type: Read-Only  
  
 The pool name. **PoolName** is valid only if the LU has already been assigned to a pool.  
  
 **Number**  
 Data Type: **sint16**Qualifiers: **MINVALUE(1), MAXVALUE(254)** Access Type: Read/Write  
  
 The LU Number for LUs on 802.2, SDLC, or X.25. For a DFT connection, **Number** is `(Port Number * 16 + LT Number)`.  
  
 **Compression**  
 Data Type: **Boolean**Access Type: Read/Write  
  
 **true** to enable 3270 LU data stream compression; otherwise, **false**. This option must also be set in the host VTAM configuration for the LU.  
  
 **UserWksSecure**  
 Data Type: **Boolean**Access Type: Read/Write  
  
 **true** to require both the user and the workstation be assigned to this LU in order to acquire it; otherwise, **false**.  
  
## Remarks  
 Each 3270 LU must belong to a connection.  
  
## Requirements  
 **Platforms**: Windows Server 2022, Windows Server 2019, Windows Server 2016, Windows 11, and Windows 10  
  
## See Also  
 [WMISNA WMI Provider Classes](../core/wmisna-wmi-provider-classes2.md)   
 [Administration and Management Programmer's Guide](./administration-and-management-programmer-s-guide2.md)
