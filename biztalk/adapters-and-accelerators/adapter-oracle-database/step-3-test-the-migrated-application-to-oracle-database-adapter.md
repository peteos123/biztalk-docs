---
description: "Learn more about: Step 3: Test the migrated application to Oracle Database adapter"
title: "Step 3: Test the migrated application to Oracle Database adapter"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Step 3: Test the migrated application to Oracle Database adapter
![Step 3 of 3](../../adapters-and-accelerators/adapter-oracle-database/media/step-3of3.gif "Step_3of3")  
  
 **Time to complete:** 5 minutes  
  
 **Objective:** In this step, you will test the migrated application by performing an Insert operation on the SCOTT.CUSTOMER table. To do this, you drop a request message that conforms to the schema generated using the vPrev Oracle Database adapter.  
  
## Prerequisites  
  
- Configure the BizTalk application by mapping the logical ports in the BizTalk orchestration to physical ports in the BizTalk Server Administration console.  
  
- Configure the BizTalk application to use the WCF-Custom send port for the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
### To test the migrated application  
  
1. From the Oracle_Migration folder, copy the OracleInsert.xml request message. This request message conforms to the schema generated by the vPrev Oracle Database adapter. Using the outbound map, the WCF-Custom send port converts this to conform to the schema for the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] and sends it to the Oracle database.  
  
   ```  
   <ns0:Insert xmlns:ns0="http://schemas.microsoft.com/[OracleDb://ADAPTER/SCOTT/Tables/CUSTOMER]">  
     <ns0:Rows>  
       <ns0:InsertRecord>  
         <ns0:NAME>Customer_1</ns0:NAME>  
         <ns0:STREET>Street_1</ns0:STREET>  
         <ns0:CITY>City_1</ns0:CITY>  
       </ns0:InsertRecord>  
       <ns0:InsertRecord>  
         <ns0:NAME>Customer_2</ns0:NAME>  
         <ns0:STREET>Street_2</ns0:STREET>  
         <ns0:CITY>City_2</ns0:CITY>  
       </ns0:InsertRecord>  
     </ns0:Rows>  
   </ns0:Insert>  
   ```  
  
2. Paste the request message to the folder mapped to the file receive location.  
  
3. The orchestration consumes the request message and sends it to the Oracle database. The response from the Oracle database is received in the schema that conforms with the schema of the WCF-based [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]. Using the inbound map, the WCF-Custom send port converts this to the schema for the vPrev Oracle Database adapter. The response from the Oracle database is saved to the other file location defined as part of the orchestration. The response for the preceding request message is:  
  
   ```  
   <?xml version="1.0" encoding="utf-8"?>  
   <ns0:InsertResponse xmlns:ns0="http://schemas.microsoft.com/[OracleDb://ADAPTER/SCOTT/Tables/CUSTOMER]"></ns0:InsertResponse>  
   ```  
  
## See Also  
 [Tutorial: Migrating BizTalk Projects](./tutorial-migrate-biztalk-projects-to-the-oracle-database-adapter.md)
