---
title: Fonction SQLTransact (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c7a4f1da36a7c233e9a1b5832ee83e86a5c1f77d
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287079"
---
# <a name="sqltransact-function"></a>SQLTransact, fonction
**Conformité**  
 Version introduite: ODBC 1.0 Standards Compliance: Deprecated  
  
 **Résumé**  
 Dans ODBC *3.x*, la fonction ODBC *2.x* **SQLTransact** a été remplacée par **SQLEndTran**. Pour plus d’informations, voir [SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md).  
  
> [!NOTE]  
>  L’attribut SQL_ASYNC_DBC_FUNCTION_ENABLE, qui a été introduit dans ODBC 3.8, n’est pas pris en charge par **SQLTransact**. Les applications utilisant une opération asynchrone sur une poignée de connexion doivent utiliser **SQLEndTran**.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
