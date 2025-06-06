---
description: "Learn more about: SQL Server Analysis Services (Troubleshooting)"
title: "SQL Server Analysis Services (Troubleshooting)2"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: troubleshooting-general
---
# SQL Server Analysis Services (Troubleshooting)
When you design cubes for use with SQL Server Analysis Services, the tools generate SQL commands that contain long alias names that may exceed the maximum length supported by the DB2 server. Depending on the DB2 platform and version that you use, you may not be able to use queries with alias names exceeding 18 characters. For example, many objects deployed in DB2 for z/OS use names of 18 characters. Refer to the DB2 SQL Reference for your DB2 platform and version and check with your DB2 database administrator. We recommend that the administrator or developer update the two SQL Server Analysis Service configuration cartridge files that contain the data type mapping support for DB2 by changing the identifier-length (limit-table-identifier-length) from 29 to 18. The following are the names and location of the two cartridge files that must be updated.  
  
 C:\Program Files\Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE\DataWarehouseDesigner\UIRdmsCartridge\db2v0801.xs  
  
 C:\Program Files\Microsoft SQL Server\100\Tools\Binn\VSShell\Common7\IDE\DataWarehouseDesigner\UIRdmsCartridge\db2v0801.xs  
  
 SQL Server Analysis Services uses the updated configuration files to correctly name objects in SQL commands.
