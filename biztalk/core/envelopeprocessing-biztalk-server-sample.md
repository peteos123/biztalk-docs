---
description: "Learn more about: EnvelopeProcessing (BizTalk Server Sample)"
title: "EnvelopeProcessing (BizTalk Server Sample)"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# EnvelopeProcessing (BizTalk Server Sample)
The EnvelopeProcessing sample demonstrates how to process messages and message envelopes in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pipelines. Further, it shows how to process flat file messages into XML messages.  

## What This Sample Does  
 This sample configures the folder EnvInput as a receive location. When you place a file, such as the sample file EnvelopeProcessing_in.txt, in this folder, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] processes the messages in this file using the following steps:  

1. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] retrieves the message file from the receive location folder EnvInput.  

2. In the receive pipeline, the Flat File Disassembler pipeline component removes the header and trailer from the flat file messages, and parses them into individual messages.  

3. In the MessageBox database, the messages are routed to the send port using subscription filters.  

4. In the send pipeline of the send port, XML Assembler pipeline component wraps the messages in XML envelopes and then places them into the send adapter folder EnvOutput.  

## How This Sample is Designed and Why  
 The design of this sample had to accommodate two basic requirements:  

- Receive and process a flat file message containing one or more purchase orders.  

- Send one XML message containing one purchase order and sender information to a directory for pickup by a back-end processing system.  

  To meet these requirements, a combination of flat file/XML schemas and custom pipelines were used. These and other design elements are summarized in the following table.  

|Design element|Reason(s) selected|  
|--------------------|--------------------------|  
|Custom receive pipeline|-   Uses the Flat File Disassembler and flat file schemas to translate inbound purchase order messages.|  
|Flat file schemas for message header, body, and trailer|-   Defines all of the same record and field characteristics (including structure) as XML schemas and provide a mechanism for defining all of the flat file characteristics that are required to translate a flat file instance message into an equivalent XML instance message (or vice versa).<br />-   Header, body, and trailer schemas are used to split the body into discrete chunks for processing.|  
|Envelope schema|-   Used to wrap individual purchase orders with information from the header.|  
|Subscription filter|-   The subscription filter performs the actual routing by capturing messages that meet one or more criteria based on property fields.|  
|Custom send pipeline|-   Uses the XML Assembler and a combination of envelope and body schemas to translate the instance messages into XML format.|  

 The following considerations apply to the design of this sample.  

-   The flat file schema (PO.xsd) contains extended annotations describing the structure of the purchase order flat file. These files can be created by hand, but many can be generated by using the Flat File Wizard.  

-   The purchase order (PO.xsd) flat file schema uses an elementFormDefault value of Unqualified. This produces correct results but with additional and unexpected xmlns qualifications. Use an elementFormDefault of Qualified to avoid this issue.  

-   Header and trailer flat file schemas are used to separate heading and trailing data from the message. The Flat File Disassembler header, document, and trailer schema properties were set to the header, purchase order, and trailer schema respectively.  

-   The XML envelope schema combines elements from the header and purchase order to produce a single XML message. The header schema promotes the Source field into the SourceParty field in the **BTS.bts_system_properties** namespace; the envelope schema promotes this same value, causing it to be demoted into the outbound message.  

## Where to Find This Sample  
 `<Samples Path>`\Pipelines\AssemblerDisassembler\EnvelopeProcessing\  

 The following table shows the files in this sample and describes their purpose.  


|                      File(s)                      |                                                                                               Description                                                                                               |
|---------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|                    Cleanup.bat                    |    Used to undeploy assemblies and remove them from the global assembly cache. Removes send and receive ports. Removes Microsoft Internet Information Services (IIS) virtual directories as needed.     |
| EnvelopeProcessing.btproj, EnvelopeProcessing.sln |                                                                               Project and solution files for this sample.                                                                               |
|             EnvelopeProcessing_in.txt             |                                                                                           Sample input file.                                                                                            |
|          Header.xsd, PO.xsd, Trailer.xsd          |                                                                      Schema for flat file header, body, and trailer, respectively.                                                                      |
|                  XmlEnvelope.xsd                  |                                                                                    Schema for outbound XML envelope.                                                                                    |
|    EnvReceivePipeline.btp, EnvSendPipeline.btp    | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive and send pipeline files with the Flat File Disassembler and XML Assembler pipeline components, respectively. |
|           EnvelopeProcessingBinding.xml           |                                                                             Used for automated setup such as port binding.                                                                              |
|                     Setup.bat                     |                                                                                Used to build and initialize this sample.                                                                                |

## How to Use This Sample  
 Use this sample as the basis for your own flat file processing solution. You can extend many of the design elements used in this sample to fit your own requirements. Some examples are as follows:  

-   Enhance the sample to write a flat file version of each purchase order in addition to the XML version. You can do this by creating a new custom send pipeline and using the Flat File Assembler. On the Flat File Assembler, specify the flat file header, purchase order, and trailer schemas. When used in a send port, it produces individual purchase orders with header/trailer information.  

-   Enhance the envelope with more information from the purchase order. To write additional information into the outbound message, promote the "ship to" name or other fields using Quick Promote, add fields to the envelope, and then promote the envelope fields to the same field. When the message is processed through the assembler, promoted properties are demoted and copied into the outbound message.  

## Building and Initializing This Sample  

#### To build and initialize the EnvelopeProcessing sample  

1. In a command window, navigate to the following folder:  

    *\<Samples Path\>*\Pipelines\AssemblerDisassembler\EnvelopeProcessing  

2. Run the file Setup.bat, which performs the following actions:  

   - Creates the input (EnvInput) and output (EnvOutput) folders for this sample in the folder:  

      *\<Samples Path\>*\Pipelines\AssemblerDisassembler\EnvelopeProcessing\  

   - Compiles and deploys the Visual Studio project for this sample.  

   - Creates and binds the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receive location, and the send and receive ports.  

      This sample displays the following warnings when creating and binding ports:  

     ```  
     Warning: Receive handler not specified for receive location "EnvelopeProcessing_RL"; updating with first receive handler with matching transport type.  
     Warning: Host not specified for orchestration "EnvelopeProcessing"; updating with first available host.  
     ```  

      You can safely ignore these warnings. (To accommodate for possible naming differences in user installations, the host name and receive handler have been omitted from the binding file.)  

   - Enables the receive location, and starts the send port.  

> [!NOTE]
>  You should confirm that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] did not report any errors during the build and initialization process before attempting to run this sample.  
> 
> [!NOTE]
>  If you choose to open and build the project in this sample without running Setup.bat, you must first create a strong name key pair using the .NET Framework Strong Name utility (sn.exe). Use this key pair to sign the resulting assembly.  
> 
> [!NOTE]
>  To undo changes made by Setup.bat, run Cleanup.bat. You must run Cleanup.bat before running Setup.bat a second time.  

## Running This Sample  

#### To run the EnvelopeProcessing sample  

1.  Put a copy of the file EnvelopeProcessing_in.txt into the folder EnvInput.  

2.  Observe the three .xml files created in the folder EnvOutput. The names of these .xml files are based on their message ID GUIDs. They contain the messages extracted from the input file and wrapped in envelopes.  

## Classes or Methods Used in This Sample  
 The configuration scripts Setup.bat and Cleanup.bat rely on the following administrative Windows Management Instrumentation (WMI) scripts:  

- Start Send Port\StartSendPort.vbs  

- Enable Receive Location\EnableRecLoc  

- Remove Send Port\RemoveSendPort  

  The setup and cleanup batch files use BTSTask as follows:  

- **BTSTask ImportBindings** to apply the binding file and create the application, ports, and bindings  

- **BTSTask RemoveApp** to remove the FlatFileReceiveApplication  

## See Also  
 [Pipelines-AssemblerDisassembler (BizTalk Server Samples Folder)](../core/pipelines-assemblerdisassembler-biztalk-server-samples-folder.md)
