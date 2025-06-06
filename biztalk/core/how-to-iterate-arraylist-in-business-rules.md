---
description: "Learn more about: How to Iterate ArrayList in Business Rules"
title: "How to Iterate ArrayList in Business Rules"
ms.custom: ""
ms.date: "06/08/2017"
ms.service: biztalk-server
ms.reviewer: ""
ms.suite: ""
ms.topic: how-to
---
# How to Iterate ArrayList in Business Rules
This section provides an example of iterating through members of an **ArrayList** in business rules.  
  
 Assume you have an **ArrayList** with a collection of **MyClass** objects. Your business rules would look like the following.  
  
## Rule A  
 IF 1==1  
  
 THEN Assert (ArrayList.GetEnumerator)  
  
 An **IEnumerator** type is asserted into the working memory, because the rule condition (1==1) always evaluates to true.  
  
## Rule B  
 IF IEnumerator.MoveNext  
  
 THEN    Assert (IEnumerator.get_Current)  
  
 Update (IEnumerator)  
  
 As the rule iterates through the **ArrayList**, each **MyClass** object in the collection is asserted into the working memory.  
  
## Rule C  
 IF MyClass.MyProperty==2  
  
 THEN \<Do Something...\>  
  
 This rule executes action(s) when the property value of the object is matched in the condition.
