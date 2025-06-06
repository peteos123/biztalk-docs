---
description: "Learn more about: Deploying Pipeline Components"
title: "Deploying Pipeline Components"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: concept-article
---
# Deploying Pipeline Components
All the .NET pipeline component assemblies (native and custom) must be located in the \<*installation directory*\>\Pipeline Components folder to be executed by the server. If the pipeline with a custom component will be deployed across several servers, the component's binaries must be present in the specified folder on every server.  
  
 You do not need to add a custom pipeline component to be used by the BizTalk Runtime to the Global Assembly Cache (GAC).  
  
 Custom COM components in the pipeline will also appear in the Toolbox, provided they are registered on the computer as a COM component. Custom .NET pipeline components must be placed into the \<*installation directory*\>\Pipeline Components folder.  
  
 After the binary files are in the correct location, you need to add the component to the Toolbox. For instructions on adding the pipeline component to the Toolbox, see [How to Use the Toolbox](../core/how-to-use-the-toolbox.md).  
  
## See Also  
 [Developing Custom Pipeline Components](../core/developing-custom-pipeline-components.md)
