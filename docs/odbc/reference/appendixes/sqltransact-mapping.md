---
description: SQLTransact, mappage
title: Mappage SQLTransact | Microsoft Docs
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
ms.openlocfilehash: cf1298c9881a207c21074e03e8b0597ab8f11448
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88429500"
---
# <a name="sqltransact-mapping"></a>SQLTransact, mappage
**SQLTransact** est maintenant remplacé par **SQLEndTran**. La principale différence entre les deux fonctions est que **SQLEndTran** contient un argument *comme HandleType*, qui spécifie l’étendue du travail à effectuer. L’argument *comme HandleType* peut spécifier l’environnement ou le handle de connexion. L’appel suivant à **SQLTransact**:  
  
```  
SQLTransact(henv, hdbc, fType)  
```  
  
 est mappé à  
  
```  
SQLEndTran(SQL_HANDLE_DBC, ConnectionHandle, CompletionType);  
```  
  
 Si *ConnectionHandle* n’est pas égal à SQL_NULL_HDBC. L’argument *ConnectionHandle* est défini sur la valeur de *hdbc*.  
  
 **SQL_Transact** est mappé à  
  
```  
SQLEndTran (SQL_HANDLE_ENV, EnvironmentHandle, CompletionType);  
```  
  
 Si *ConnectionHandle* est égal à SQL_NULL_HDBC. L’argument *EnvironmentHandle* est défini sur la valeur de *henv*.  
  
 Dans les deux cas précédents, l’argument *CompletionType* est défini sur la même valeur que *ftype*.
