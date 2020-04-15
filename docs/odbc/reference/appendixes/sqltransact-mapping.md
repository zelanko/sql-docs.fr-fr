---
title: Cartographie SQLTransact Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6aaa056fca860a70f81ad7c3a4cd8539512bc25d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304880"
---
# <a name="sqltransact-mapping"></a>SQLTransact, mappage
**SQLTransact** est maintenant remplacé par **SQLEndTran**. La principale différence entre les deux fonctions est que **SQLEndTran** contient un argument *HandleType*, qui spécifie la portée du travail à faire. *L’argument De HandleType* peut spécifier l’environnement ou la poignée de connexion. L’appel suivant à **SQLTransact**:  
  
```  
SQLTransact(henv, hdbc, fType)  
```  
  
 est cartographié pour  
  
```  
SQLEndTran(SQL_HANDLE_DBC, ConnectionHandle, CompletionType);  
```  
  
 si *ConnectionHandle* n’est pas égal à SQL_NULL_HDBC. *L’argument ConnectionHandle* est réglé à la valeur de *hdbc*.  
  
 **SQL_Transact** est cartographié pour  
  
```  
SQLEndTran (SQL_HANDLE_ENV, EnvironmentHandle, CompletionType);  
```  
  
 si *ConnectionHandle* est égal à SQL_NULL_HDBC. *L’argument de EnvironmentHandle* est fixé à la valeur du *henv*.  
  
 Dans les deux cas précédents, l’argument *de CompletionType* est réglé à la même valeur que *fType*.
