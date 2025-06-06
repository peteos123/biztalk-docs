---
description: "Learn more about: Message Schema for Picklist Operations"
title: "Message Schema for Picklist Operations"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Message Schema for Picklist Operations
Picklists are special field types in business components. They represent a collection of values from which a user may pick a single value for assignment. Picklists are of different types. For more information about picklists and their types, refer to Siebel documentation.  
  
 One of the picklist types, static bounded picklists, are surfaced by the adapters as an enumerated picklist type in the metadata generated by the adapter at design time. This contains a static set of values that must be specified for the picklist type at run time.  While specifying a value for a static bounded picklist, you must always specify a value that belongs to the set.  
  
 The following sample shows the schema of a static bounded picklist type:  
  
```  
<element name="[FIELD_NAME]RequiredPickListType" nillable="true" type="ns1:[FIELD_NAME]RequiredPickListType" />  
<simpleType name="[FIELD_NAME]RequiredPickListType">  
<restriction base="string">  
  <enumeration value="value1" />  
  <enumeration value="value2" />  
  …  
</restriction>  
</simpleType>  
```  
  
 [FIELD_NAME] = Picklist field name in the business component  
  
 The following represents the proxy experience of a static bounded picklist type:  
  
```  
[BC]InsertRecord[] insertRecs = new [BC]InsertRecord[1];  
insertRecs[0] = new [BC]InsertRecord();  
insertRecs[0].[BC_STATIC_PICKLIST_FIELD] = [BC_PICKLIST_FIELD_NAME]OptionalPickListType.value1;  
```  
  
 [BC_STATIC_PICKLIST_FIELD] = A static bounded picklist field in the BC  
  
## See Also  
 [Messages and Message Schemas for BizTalk Adapter for Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/messages-and-message-schemas-for-siebel-adapter-in-biztalk.md)
