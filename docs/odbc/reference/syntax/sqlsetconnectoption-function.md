---
title: Fonction SQLSetConnectOption (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetConnectOption
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetConnectOption
helpviewer_keywords:
- SQLSetConnectOption function [ODBC]
ms.assetid: 8cd2c2a2-25c8-4aff-951c-b593bbfc90ad
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 263b15cb75fb5c0c7c1d7aa630a8da171b9765a7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301594"
---
# <a name="sqlsetconnectoption-function"></a>SQLSetConnectOption, fonction
**Conformité**  
 Version introduite: ODBC 1.0 Standards Compliance: Deprecated  
  
 **Résumé**  
 Dans ODBC 3 *.x*, la fonction ODBC 2.0 **SQLSetConnectOption** a été remplacée par **SQLSetConnectAttr**. Pour plus d’informations, consultez [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
> [!NOTE]
>  Pour plus d’informations sur ce que le Driver Manager cartographie cette fonction à quand une application ODBC 2 *.x* travaille avec un pilote ODBC 3 *.x,* voir [Mapping Deprecated Functions](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)".  
  
## <a name="remarks"></a>Notes  
 Consultez [ODBC 64-Bit Information](../../../odbc/reference/odbc-64-bit-information.md), si votre application s’exécute sur un système d’exploitation 64 bits.  
  
> [!NOTE]  
>  L’attribut SQL_ASYNC_DBC_FUNCTION_ENABLE introduit dans ODBC 3.8 n’est pas pris en charge par **SQLSetConnectOption**. Les applications qui utilisent l’opération asynchrone sur la poignée de connexion doivent utiliser **SQLSetConnectAttr**.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
