---
description: "Learn about the attributes, child elements, and parent elements of the db2ToSql element that defines the direction from DB2 to SQL Server."
title: "db2ToSql1"
ms.custom: ""
ms.date: "11/30/2017"
ms.service: host-integration-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# About db2ToSql

The db2ToSql defines the direction from DB2 to SQL Server.  
  
 \<hostIntegration.drdaAs.drdaService>  
\<services>  
\<service>  
\<conversionFormats>  
\<timeMasks>  
\<timeMask>  
  
## Syntax  
  
```xml  
<hostIntegration.drdaAs.drdaService>
    <services>
         <service>
              <conversionFormats>
                   <timeMasks> 
                        <timeMask> 
                             <db2ToSql>  
                             </db2ToSql>  
                        </timeMask>    
                   </timeMasks>       
              </conversionFormats>    
         </service>   
    </services>
</hostIntegration.drdaAs.drdaService>  
```  
  
## Attributes and Elements
  
The following sections describe attributes, child elements, and parent elements.  
  
### Attributes  
  
|Attribute|Type|Description|Required|Default Value|  
|---------------|----------|-----------------|--------------|-------------------|  
|sourceFormat|drdaas:TimeFormats||true|n/a|  
  
### Child Elements
  
None  
  
### Parent Elements  
  
|Element|Description|  
|-------------|-----------------|  
||The timeMask element contains a db2ToSql or sqlToDb2 to indicate the direction, and a sourceFormat and a targetFormat to specify the mapping.|
