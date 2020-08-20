---
description: SQLRemoveDefaultDataSource, fonction
title: SQLRemoveDefaultDataSource fonction) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLRemoveDefaultDataSource
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLRemoveDefaultDataSource
helpviewer_keywords:
- SQLRemoveDefaultDataSource function [ODBC]
ms.assetid: db803266-57df-4864-a41b-901247549c1f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0010e59cc4dfad2d54b8b1c4e59e83ea72fcd3ad
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88487087"
---
# <a name="sqlremovedefaultdatasource-function"></a>SQLRemoveDefaultDataSource, fonction
**Conformité**  
 Version introduite : ODBC 1,0, déconseillé  
  
 **Résumé**  
 Dans ODBC 3,0, la fonction **SQLRemoveDefaultDataSource** a été remplacée par un appel à [SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md) avec un argument *fRequest* de ODBC_REMOVE_DEFAULT_DSN. Si un programme d’installation ODBC 2 *. x* appelle cette fonction, le programme d’installation ODBC le mappe à l’appel de **SQLConfigDataSource** suivant :  
  
```cpp  
SQLConfigDataSource (NULL, ODBC_REMOVE_DEFAULT_DSN, NULL, NULL)  
```
