---
title: Mappage de SQLTransact | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLTransact
- SQLTransact function [ODBC], mapping
ms.assetid: 8a01041f-3572-46f9-8213-b817f3cf929c
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 252339f7fcd2a3893f030c0ffbc4485ab5441152
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="sqltransact-mapping"></a>Mappage de SQLTransact
**SQLTransact** est désormais remplacée par **SQLEndTran**. La principale différence entre les deux fonctions est que **SQLEndTran** contient un argument *HandleType*, qui spécifie la portée du travail à faire. Le *HandleType* argument peut spécifier l’environnement ou le handle de connexion. L’appel suivant à **SQLTransact**:  
  
```  
SQLTransact(henv, hdbc, fType)  
```  
  
 est mappée à  
  
```  
SQLEndTran(SQL_HANDLE_DBC, ConnectionHandle, CompletionType);  
```  
  
 Si *handle de connexion* n’est pas égal à SQL_NULL_HDBC. Le *handle de connexion* argument est défini à la valeur de *pas*.  
  
 **SQL_Transact** est mappé à  
  
```  
SQLEndTran (SQL_HANDLE_ENV, EnvironmentHandle, CompletionType);  
```  
  
 Si *handle de connexion* est égal à SQL_NULL_HDBC. Le *EnvironmentHandle* argument est défini à la valeur de *henv*.  
  
 Dans les deux cas précédents, les *CompletionType* argument est défini sur la même valeur que *fType*.

