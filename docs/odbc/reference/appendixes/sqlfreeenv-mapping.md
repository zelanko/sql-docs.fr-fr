---
title: Mappage de SQLFreeEnv | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLFreeEnv function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLFreeEnv
ms.assetid: c0f76455-d072-4bae-bee7-452277dfa479
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: c2aa64e5ca6e64932c4362603dc370ab02f7c962
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="sqlfreeenv-mapping"></a>Mappage de SQLFreeEnv
Lorsqu’une application appelle **SQLFreeEnv** via un ODBC 3*.x* pilote, l’appel à  
  
```  
SQLFreeEnv(henv)   
```  
  
 est mappée à  
  
```  
SQLFreeHandle(SQL_HANDLE_ENV,Handle)  
```  
  
 avec la *gérer* affectée à la valeur de l’argument *henv*.
