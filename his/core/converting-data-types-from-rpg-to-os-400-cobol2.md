---
description: "Learn more about: Converting Data Types from RPG to IBM i COBOL"
title: "Converting Data Types from RPG to OS-400 COBOL2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Converting Data Types from RPG to IBM i COBOL
The Transaction Integrator (TI) run-time environment supports the use of IBM i COBOL running on an IBM i computer. The following table lists the Report Program Generator ( to  data type conversions supported by the TI run-time environment.  
  
|RPG data type|IBM i COBOL data type|  
|-------------------|-----------------------------|  
|Type A|PIC X|  
|Type G|PIC G|  
|Type S|PIC S99v99 Display|  
|Type L **Note:**  Type L is not supported by the TI run-time environment.|PIC S99v99 Display Sign Leading Separate|  
|Type R **Note:**  Type R is not supported by the TI run-time environment.|PIC S99v99 Display Sign Trailing Separate|  
|Type P|PIC S99v99 Comp|  
|Type B **Note:**  Type B is not supported by the TI run-time environment.|PIC S99V99 Comp|  
|Type I 5 digits|PIC S9(1) to S9(4) Comp-3|  
|Type U 5 digits **Note:**  Type U 5 is not supported by the TI run-time environment. Use Type I 5 instead.|PIC 9(1) to 9(4) Comp-3|  
|Type I 10|PIC S9(5) to S9(9) Comp-3|  
|Type U 10 **Note:**  Type U 10 is not supported by the TI run-time environment. Use Type I 10 instead.|PIC 9(5) to 9(9) Comp-3|  
|Type F 4|COMP-1|  
|Type F 8|COMP-2|  
|Type D|None|  
|Type T|None|  
|Type Z|None|  
  
## See Also  
 [Supported TI Data Types](../core/supported-ti-data-types2.md)   
 [Data Type Conversion](../core/data-type-conversion1.md)
