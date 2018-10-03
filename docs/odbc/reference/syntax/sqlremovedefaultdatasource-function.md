---
title: Sqlremovedefaultdatasource, fonction | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 90270f119b351592348287823c2b9d879a15154b
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47821117"
---
# <a name="sqlremovedefaultdatasource-function"></a>SQLRemoveDefaultDataSource, fonction
**Conformité**  
 Version introduite : ODBC 1.0, déconseillée  
  
 **Résumé**  
 Dans ODBC 3.0, le **SQLRemoveDefaultDataSource** fonction a été remplacée par un appel à [SQLConfigDataSource](../../../odbc/reference/syntax/sqlconfigdatasource-function.md) avec un *fréquents* argument de ODBC_REMOVE_DEFAULT_DSN. Si un ODBC 2 *.x* programme d’installation appelle cette fonction, le programme d’installation ODBC mappera à ce qui suit **SQLConfigDataSource** appeler :  
  
```  
SQLConfigDataSource (NULL, ODBC_REMOVE_DEFAULT_DSN, NULL, NULL)  
```
