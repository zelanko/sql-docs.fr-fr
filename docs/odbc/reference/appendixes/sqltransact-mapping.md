---
title: Mappage de SQLTransact | Documents Microsoft
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
- mapping deprecated functions [ODBC], SQLTransact
- SQLTransact function [ODBC], mapping
ms.assetid: 8a01041f-3572-46f9-8213-b817f3cf929c
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e4742829b5df9d99007181109f68d020a2f4af98
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
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
