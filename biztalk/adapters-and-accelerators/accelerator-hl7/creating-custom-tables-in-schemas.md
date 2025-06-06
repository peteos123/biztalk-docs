---
description: "Learn more about: Creating Custom Tables in Schemas"
title: "Creating Custom Tables in Schemas"
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.topic: how-to
---
# Creating Custom Tables in Schemas
You can create a custom table in the tablevalues_\<*version*\>.xsd common schema. You can base a custom table on an existing data type, a base data type, or on an enumeration defined in a table.  
  
### To create a Z table  
  
1.  In Solution Explorer, open the common data-type schema file **tablevalues_\<*version*\>.xsd**, and then click **Open**.  
  
2.  In BizTalk Editor, right-click **HL7DefinedTables**, point to **Insert Schema Node**, and then click **Child Field Element**.  
  
3.  Name the table with a tag starting with the letter "Z".  
  
4.  In the Properties pane, type the values you want for specific properties, as needed.  
  
5.  To associate an enumeration with the table, in the Properties pane, set **Derived By** to **Restriction**, click **Enumeration**, click the ellipsis (…) button for **Enumeration**, and then type the values that you want the enumeration to contain in the Enumeration Editor. Click **OK**.  
  
## See Also  
 [Extending HL7 2.X Schemas with Z Objects](../../adapters-and-accelerators/accelerator-hl7/extending-hl7-2-x-schemas-with-z-objects.md)   
 [Creating Declared Z Segments](../../adapters-and-accelerators/accelerator-hl7/creating-declared-z-segments.md)   
 [Creating Custom Data Types in Schemas](../../adapters-and-accelerators/accelerator-hl7/creating-custom-data-types-in-schemas.md)   
 [Extending Enumerations](../../adapters-and-accelerators/accelerator-hl7/extending-enumerations.md)   
 [Handling Undeclared Z Segments](../../adapters-and-accelerators/accelerator-hl7/handling-undeclared-z-segments.md)
