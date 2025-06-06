---
description: "Learn more about: Generating an Instance (EDI)"
title: "Generating an Instance (EDI)"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Generating an Instance (EDI)
You can generate a message instance from an EDI schema at design time. To do so, you use the XML Tool extensions to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] environment.  
  
 You can generate either a complete batched interchange (with interchange and group headers) or a transaction set (without interchange and group headers). If you execute the operation to generate a complete interchange, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will generate a file with one interchange header, a group for each schema, and three identical transaction sets per group for each schema. If you execute the operation to generate a transaction set, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will generate a file with a single transaction set.  
  
 To generate a complete batched interchange, you execute the generate-instance command on the batch schema. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will detect the message schemas in the project, and will automatically include transaction sets for those schemas.  
  
 To generate a single transaction set, you execute the generate-instance command on a message schema. In this case, the batch schema does not need to be added to the project. The generated instance will not include an interchange or group header, however, so you will have to add those manually to have a functional EDI interchange.  
  
 When you generate an instance, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] displays a dialog box in which you specify the configuration used in that instance, including separators and the syntax identifier.  
  
## Prerequisites  
 You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.  
  
### To generate an instance of a batched interchange  
  
1. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open a project. Add a message schema to the project in Solution Explorer for each type of transaction set that you want in the message instance. Add the batch schema for the type of encoding to the project: either Edifact_BatchSchema.xsd or X12_BatchSchema.xsd.  
  
   > [!NOTE]
   >  The batch schemas are located in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI folder.  
   > 
   > [!NOTE]
   >  You do not have to build the project to generate an instance.  
  
2. Right-click the batch schema in Solution Explorer, and then click **Properties**.  
  
3. In the **Properties** window, set **Generate Instance Output Type** to **Native** or **XML**. Selecting **Native** will prompt generation of a flat file with a .txt extension. Selecting **XML** will prompt generation of an XML file.  
  
4. For **Output Instance Filename**, enter a name or browse to a file and select the file.  
  
   > [!NOTE]
   >  If you do not enter a value for the output instance filename, one will be chosen for you. The filename will be displayed in the Output window of [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
   > 
   > [!NOTE]
   >  If you select an existing file, the contents of the existing file will be replaced with the content generated by this operation.  
  
5. Right-click the batch schema and then click **Generate Instance**.  
  
6. In the **EDI Instance Properties** dialog box, select the separators, identifiers, and other configuration options to be used in that instance, and then click **OK**.  
  
7. Verify that the operation worked in the **Output** window.  
  
8. To view the file, press **Control** and click the link in the **Output** window. [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] will display the contents of the file in the BizTalk Editor window.  
  
   > [!NOTE]
   >  When generating an instance that contains an 837I, 837D, or 837P, the value of GS08 will be incorrectly set to 00401. For more information, see [Known Issues with XML Tools Used with EDI Solutions](../core/known-issues-with-xml-tools-used-with-edi-solutions.md).  
  
### To generate an instance of a transaction set  
  
1. In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], open a project. Add the schema for the type of transaction set that you want to generate an instance for.  
  
   > [!NOTE]
   >  You do not have to add the batch schema to the project to generate an instance of a transaction set.  
  
   > [!NOTE]
   >  You do not have to build the project to generate an instance.  
  
2. Right-click the message schema in Solution Explorer, and then click **Properties**.  
  
3. In the Properties window, set **Generate Instance Output Type** to **Native** or **XML**. Selecting **Native** will prompt generation of a flat file with a .txt extension. Selecting **XML** will prompt generation of an XML file.  
  
4. For **Output Instance Filename**, enter a name or browse to a file and select the file.  
  
   > [!NOTE]
   >  If you do not enter a value for the output instance filename, one will be chosen for you. The filename will be displayed in the **Output** window of [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
   > 
   > [!NOTE]
   >  If you select an existing file, the contents of the existing file will be replaced with the content generated by this operation.  
  
5. Right-click the message schema and then click **Generate Instance**.  
  
6. In the **EDI Instance Properties** dialog box, select the configuration options that you want, and then click **OK**.  
  
7. Verify that there is a message in the **Output** window indicating that the operation succeeded.  
  
8. To view the file, press **Control** and click the link in the Output window. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will display the contents of the file in the BizTalk Editor window.  
  
9. To make a functional EDI message, add the interchange and group headers to the message in a text editor.  
  
## See Also  
 [Using Design-Time XML Tools](../core/using-design-time-xml-tools.md)   
 [Validating an Instance (EDI)](../core/validating-an-instance-edi.md)
