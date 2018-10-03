---
title: SQLTransact, mappage | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLTransact
- SQLTransact function [ODBC], mapping
ms.assetid: 8a01041f-3572-46f9-8213-b817f3cf929c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d5cf669883ce81528adbe1fbd8faeff2ed716218
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47656175"
---
# <a name="sqltransact-mapping"></a>SQLTransact, mappage
**SQLTransact** est désormais remplacée par **SQLEndTran**. La principale différence entre les deux fonctions est que **SQLEndTran** contient un argument *HandleType*, qui spécifie la portée du travail à faire. Le *HandleType* argument peut spécifier l’environnement ou le handle de connexion. L’appel suivant à **SQLTransact**:  
  
```  
SQLTransact(henv, hdbc, fType)  
```  
  
 est mappé à  
  
```  
SQLEndTran(SQL_HANDLE_DBC, ConnectionHandle, CompletionType);  
```  
  
 Si *ConnectionHandle* n’est pas égal à SQL_NULL_HDBC. Le *ConnectionHandle* argument est défini sur la valeur de *pas*.  
  
 **SQL_Transact** est mappé à  
  
```  
SQLEndTran (SQL_HANDLE_ENV, EnvironmentHandle, CompletionType);  
```  
  
 Si *ConnectionHandle* est égal à SQL_NULL_HDBC. Le *EnvironmentHandle* argument est défini sur la valeur de *henv*.  
  
 Dans les deux cas précédents, le *CompletionType* argument est défini sur la même valeur que *fType*.
