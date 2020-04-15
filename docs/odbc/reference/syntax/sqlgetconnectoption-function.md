---
title: Fonction SQLGetConnectOption (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLGetConnectOption
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLGetConnectOption
helpviewer_keywords:
- SQLGetConnectOption function [ODBC]
ms.assetid: 59cde899-7957-4b5e-8677-f34d3b859bfd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 94a29637365862990ea067f663023fae04a7af3e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285569"
---
# <a name="sqlgetconnectoption-function"></a>SQLGetConnectOption, fonction
**Conformité**  
 Version introduite: ODBC 1.0 Standards Compliance: Deprecated  
  
 **Résumé**  
 Dans ODBC *3.x*, la fonction ODBC *2.x* **SQLGetConnectOption** a été remplacée par **SQLGetConnectAttr**. Pour plus d’informations, voir [SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md).  
  
> [!NOTE]
>  Pour plus d’informations sur ce que le Gestionnaire de conducteur cartographie cette fonction à quand une application ODBC *2.x* travaille avec un pilote ODBC *3.x,* voir [Mapping Deprecated Functions](../../../odbc/reference/appendixes/mapping-deprecated-functions.md) in Appendix G: Driver Guidelines for Backward Compatibility.  
> 
> [!NOTE]
>  L’attribut SQL_ASYNC_DBC_FUNCTION_ENABLE introduit dans ODBC 3.8 n’est pas pris en charge par **SQLGetConnectOption**. Les applications qui utilisent l’opération asynchrone sur une poignée de connexion doivent utiliser **SQLGetConnectAttr**.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
