---
description: "Learn more about: CMDSemSet"
title: "CMDSemSet1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/30/2017"
ms.prod: "host-integration-server"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ecb73d36-143f-45da-b139-d750b010f441
caps.latest.revision: 3
author: "christopherhouser"
ms.author: "hisdocs"
manager: "anneta"
---
# CMDSemSet
The **CMDSemSet** function sets a RAM semaphore.  
  
## Syntax  
  
```  
  
USHORT FAR CMDSemSet(   
ULONG FAR *ramSem   
);  
```  
  
#### Parameters  
 *ramSem*  
 Address of the semaphore.
