---
title: Mappage de SQLAllocConnect | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLAllocConnect function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLAllocConnect
ms.assetid: ac89dd1f-c565-47cc-8fa3-6fa5f80b5d63
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 001c430558b3db813bd316f3b4d913fe0eae26c2
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="sqlallocconnect-mapping"></a>Mappage de SQLAllocConnect
Lorsqu’une application appelle **SQLAllocConnect** via un ODBC 3. *x* pilote, l’appel à **SQLAllocConnect**(*henv*, *phdbc*) est mappée à **SQLAllocHandle** comme suit :  
  
1.  Le Gestionnaire de pilotes alloue une connexion et le retourne à l’application.  
  
2.  Lorsque l’application établit une connexion, le Gestionnaire de pilotes appelle  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_DBC, InputHandle, OutputHandlePtr)  
    ```  
  
     dans le pilote avec *InputHandle* la valeur *henv*, et *OutputHandlePtr* la valeur *phdbc*.
