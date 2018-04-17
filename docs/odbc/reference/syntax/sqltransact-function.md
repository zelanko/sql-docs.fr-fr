---
title: Fonction de SQLTransact | Documents Microsoft
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
apiname:
- SQLTransact
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLTransact
helpviewer_keywords:
- SQLTransact function [ODBC]
ms.assetid: 496249e0-8eff-4c60-8358-5543bc3ead9c
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 30aec4f94ca469f46ea4da6636c847d4a663dc3c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="sqltransact-function"></a>SQLTransact (fonction)
**Mise en conformité**  
 Version introduite : Conformité de normes 1.0 ODBC : déconseillé  
  
 **Résumé**  
 Dans ODBC 3. *x*, ODBC 2*.x* fonction **SQLTransact** a été remplacé par **SQLEndTran**. Pour plus d’informations, consultez [SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).  
  
> [!NOTE]  
>  Ne prend pas en charge l’attribut SQL_ASYNC_DBC_FUNCTION_ENABLE, qui a été introduite dans ODBC 3.8, **SQLTransact**. Les applications à l’aide d’une opération asynchrone sur un handle de connexion doivent utiliser **SQLEndTran**.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
