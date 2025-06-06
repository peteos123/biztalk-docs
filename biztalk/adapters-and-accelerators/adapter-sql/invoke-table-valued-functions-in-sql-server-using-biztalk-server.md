---
description: "Learn more about: Invoke Table-Valued Functions in SQL Server using BizTalk Server"
title: "Invoke Table-Valued Functions in SQL Server using BizTalk Server"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# Invoke Table-Valued Functions in SQL Server using BizTalk Server
You can use the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] to invoke table-valued functions in SQL Server. The adapter exposes the table-valued functions as operations that can be invoked directly on SQL Server. For more information about how the adapter supports table-valued functions, see [Executing Table-Valued Functions in SQL Server using the SQL adapter](../../adapters-and-accelerators/adapter-sql/execute-table-valued-functions-in-sql-server-using-the-sql-adapter.md). For information about the structure of the SOAP message for invoking table-valued functions, see [Message Schemas for Procedures and Functions](../../adapters-and-accelerators/adapter-sql/message-schemas-for-procedures-and-functions.md).  
  
## Prerequisites  
  
- Create a [strong-name key file, and learn the tools](prerequisites-to-create-sql-applications-using-the-sql-adapter.md)
  
- [Configure MSDTC](configure-msdtc-on-sql-server-and-adapter-client.md) on computers running the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] and SQL Server.
  
## Invoke Table-valued Functions on a SQL Server Database  
 Performing an operation on a SQL Server database by using [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] involves procedural tasks described in [Building blocks to develop BizTalk applications with the SQL adapter](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md). To invoke table-valued functions in SQL Server, these tasks are:  
  
1. Create a BizTalk project, and generate schema for the table-valued function you want to invoke in SQL Server.  
  
2. Create messages in the BizTalk project for sending and receiving messages from SQL Server.  
  
3. Create an orchestration to invoke the operation on SQL Server.  
  
4. Build and deploy the BizTalk project.  
  
5. Configure the BizTalk application by creating physical send and receive ports.  
  
6. Start the BizTalk application.  
  
   This topic provides instructions to perform these tasks.  
  
## Generate Schema  
 This topic demonstrates how to invoke table-valued functions in SQL Server using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. To demonstrate this operation, in this topic you execute the TVF_EMPLOYEE function. This function takes an employee’s designation as a parameter and returns all the employee records with that designation, as a table type. The Employee table and the function are created by running the scripts provided with the samples. For more information about the script, see [Samples for the SQL adapter](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md).  
  
 To demonstrate how to invoke table-valued functions, schema is generated for the TVF_EMPLOYEE table-valued function. You must create a BizTalk project and use the [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] to generate the schema. See [Retrieving Metadata for SQL Server Operations in Visual Studio using the SQL adapter](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md) for more information about how to generate schemas.  
  
## Define Messages and Message Types  
 The schema that you generated earlier describes the “types” required for the messages in the orchestration. A message is typically a variable, the type for which defined by the corresponding schema. Now, create messages for the orchestration and link them to schemas you generated in the previous step.  
  
1.  Add an orchestration to the BizTalk project. From Solution Explorer, right-click the BizTalk project name, point to **Add**, and then click **New Item**. Type a name for the BizTalk orchestration, and then click **Add**.  
  
2.  Open the Orchestration View window of the BizTalk project, if it is not already open. To do so, click **View**, point to **Other Windows**, and then click **Orchestration View**.  
  
3.  In Orchestration View, right-click **Messages**, and then click **New Message**.  
  
4.  Right-click the newly created message, and then select **Properties Window**.  
  
5.  In the **Properties** pane for the **Message_1**, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |Identifier|Type `Request`|  
    |Message Type|From the drop-down list, expand **Schemas**, and then select *TableFunctions.TableValuedFunction_dbo.TVF_EMPLOYEE*, where TableFunctions is the name of your BizTalk project. TableValuedFunction_dbo is the schema generated for the TVF_EMPLOYEE function.|  
  
6.  Repeat step 2 to create a new message. In the **Properties** pane for the new message, do the following:  
  
    |Use this|To do this|  
    |--------------|----------------|  
    |Identifier|Type `Response`|  
    |Message Type|From the drop-down list, expand **Schemas**, and then select *TableFunctions.TableValuedFunction_dbo.TVF_EMPLOYEEResponse*.|  
  
## Set up the Orchestration  
 Create a BizTalk orchestration to use [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] for performing an operation on SQL Server. In this orchestration, you drop a request message at a defined receive location. The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] consumes this message and passes it on to SQL Server. The response from SQL Server is saved to another location. You must include Send and Receive shapes to send messages to SQL Server and to receive responses, respectively. A sample orchestration for invoking a table-valued function resembles the following:  
  
 ![Orchestration for invoking a table&#45;valued function](../../adapters-and-accelerators/adapter-sql/media/28ca3930-7ce8-423a-9edd-cb2888eebaac.gif "28ca3930-7ce8-423a-9edd-cb2888eebaac")  
  
### Add Message Shapes  
 Enter the following properties for each of the message shapes. The names listed in the Shape column are the names of the message shapes as displayed in the just-mentioned orchestration.  
  
|Shape|Shape Type|Properties|  
|-----------|----------------|----------------|  
|ReceiveMessage|Receive|-   Set **Name** to *ReceiveMessage*<br />-   Set **Activate** to *True*|  
|SendMessage|Send|-   Set **Name** to *SendMessage*|  
|ReceiveResponse|Receive|-   Set **Name** to *ReceiveResponse*<br />-   Set **Activate** to *False*|  
|SendResponse|Send|-   Set **Name** to *SendResponse*|  
  
### Add Ports  
 Enter the following properties for each of the logical ports. The names listed in the Port column are the names of the ports as displayed in the orchestration.  
  
|Port|Properties|  
|----------|----------------|  
|MessageIn|-   Set **Identifier** to *MessageIn*<br />-   Set **Type** to *MessageInType*<br />-   Set **Communication Pattern** to *One-Way*<br />-   Set **Communication Direction** to *Receive*|  
|LOBPort|-   Set **Identifier** to *LOBPort*<br />-   Set **Type** to *LOBPortType*<br />-   Set **Communication Pattern** to *Request-Response*<br />-   Set **Communication Direction** to *Send-Receive*|  
|ResponseOut|-   Set **Identifier** to *ResponseOut*<br />-   Set **Type** to *ResponseOutType*<br />-   Set **Communication Pattern** to *One-Way*<br />-   Set **Communication Direction** to *Send*|  
  
### Enter Messages for Action Shapes, and Connect Them to Ports  
 The following table specifies the properties and their values that you should set to specify messages for action shapes and to link the messages to the ports. The names listed in the Shape column are the names of the message shapes as displayed in the orchestration mentioned earlier.  
  
|Shape|Properties|  
|-----------|----------------|  
|ReceiveMessage|-   Set **Message** to *Request*<br />-   Set **Operation** to *MessageIn.TVF.Request*|  
|SendMessage|-   Set **Message** to *Request*<br />-   Set **Operation** to *LOBPort.TVF.Request*|  
|ReceiveResponse|-   Set **Message** to *Response*<br />-   Set **Operation** to *LOBPort.TVF.Response*|  
|SendResponse|-   Set **Message** to *Response*<br />-   Set **Operation** to *ResponseOut.TVF.Request*|  
  
 After you have specified these properties, the message shapes and ports are connected, and your orchestration is complete.  
  
 Now, build the BizTalk solution, and deploy it to BizTalk Server. For more information, see [Building and Running Orchestrations](../../core/building-and-running-orchestrations.md).
  
## Configure the BizTalk Application  
 After you have deployed the BizTalk project, the orchestration you created earlier is listed under the Orchestrations pane in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console. You must use the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console to configure the application. For a walkthrough, see [Walkthrough: Deploying a Basic BizTalk Application](../../core/walkthrough-deploying-a-basic-biztalk-application.md).
 
 Configuring an application involves:  
  
- Selecting a host for the application.  
  
- Mapping the ports that you created in your orchestration to physical ports in the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console. For this orchestration you must:  
  
  - Define a location on the hard disk and a corresponding file port where you will drop a request message. The BizTalk orchestration will consume the request message and send it to the SQL Server database.  
  
  - Define a location on the hard disk and a corresponding file port where the BizTalk orchestration will drop the response message containing the response from the SQL Server database.  
  
  - Define a physical WCF-Custom or WCF-SQL send port to send messages to the SQL Server database. You must also specify the action in the send port. For information about how to create ports, see [Manually configure a physical port binding to the SQL adapter](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md).
  
    > [!NOTE]
    >  Generating the schema using the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] also creates a binding file that contains information about the ports and the actions to be set for those ports. You can import this binding file from the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] Administration console to create send ports (for outbound calls) or receive ports (for inbound calls). For more information, see [Configure a physical port binding using a port binding file to use the SQL adapter](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md).
  
## Start the Application  
 Start the BizTalk application for invoking table-valued functions in the SQL Server database. For instructions on starting a BizTalk application, see [How to Start an Orchestration](../../core/how-to-start-an-orchestration.md).
  
 At this stage, make sure:  
  
-   The FILE receive port to receive request messages for the orchestration is running.  
  
-   The FILE send port to receive the response messages from the orchestration is running.  
  
-   The WCF-Custom or WCF-SQL send port to send messages to the SQL Server database is running.  
  
-   The BizTalk orchestration for the operation is running.  
  
## Execute the Operation  
 After you run the application, you must drop a request message to the FILE receive location. The schema for the request message must conform to the schema for the TVF_EMPLOYEE table-valued function you generated earlier. For example, the request message to invoke the TVF_EMPLOYEE function is:  
  
```  
<TVF_EMPLOYEE xmlns="http://schemas.microsoft.com/Sql/2008/05/TableValuedFunctions/dbo">  
  <emp_desig>Tester</emp_desig>  
</TVF_EMPLOYEE>  
```  
  
 This request message invokes the TVF_EMPLOYEE function to retrieve employee records having the designation as “Tester”. See [Message Schemas for Procedures and Functions](../../adapters-and-accelerators/adapter-sql/message-schemas-for-procedures-and-functions.md) for more information about the request message schema for invoking table-valued functions in SQL Server using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
> [!NOTE]
>  If you do not specify a value for the parameter the adapter internally executes the function using the DEFAULT keyword, which means that the adapter executes the function by passing the default value for the parameter, if available as part of the function definition.  
  
 The orchestration consumes the message and sends it to the SQL Server database. The response from the SQL Server database is saved at the other FILE location defined as part of the orchestration. For example, the response from the SQL Server database for the preceding request message is:  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<TVF_EMPLOYEEResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/TableValuedFunctions/dbo">  
  <TVF_EMPLOYEEResult>  
    <TVF_EMPLOYEE xmlns="http://schemas.microsoft.com/Sql/2008/05/Types/TableFunctionReturnTables/dbo">  
      <Employee_ID>10499</Employee_ID>   
      <Name>John</Name>   
      <Designation>Tester</Designation>   
      <Salary>999999.00</Salary>   
      <Last_Modified>AAAAAAAAJBM=</Last_Modified>   
    </TVF_EMPLOYEE>  
    <TVF_EMPLOYEE xmlns="http://schemas.microsoft.com/Sql/2008/05/Types/TableFunctionReturnTables/dbo">  
      ......  
      ......  
    </TVF_EMPLOYEE>  
    ......  
    ......  
  </TVF_EMPLOYEEResult>  
</TVF_EMPLOYEEResponse>  
```  
  
## Best Practices  
 After you have deployed and configured the BizTalk project, you can export configuration settings to an XML file called the binding file. Once you generate a binding file, you can import the configuration settings from the file, so that you do not need to create items such as the send ports and receive ports for the same orchestration. For more information about binding files, see [Reuse adapter bindings](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md).
  
## See Also  
[Develop BizTalk applications using the SQL adapter](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md)
