---
title: Mappage de SQLFreeEnv | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQLFreeEnv function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLFreeEnv
ms.assetid: c0f76455-d072-4bae-bee7-452277dfa479
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 0746ec836f95223c1ed1090a827675b3f16f1200
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
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
