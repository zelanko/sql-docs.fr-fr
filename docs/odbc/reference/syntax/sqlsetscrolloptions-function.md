---
title: Fonction SQLSetScrollOptions (fr) Microsoft Docs
ms.custom: ''
ms.date: 07/18/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLSetScrollOptions
apilocation:
- sqlsrv32.dll
- odbc32.dll
apitype: dllExport
f1_keywords:
- SQLSetScrollOptions
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC]
ms.assetid: 2a825ba7-7942-4c23-bcdb-c80dc12f8c86
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 056fc203581e1d5d8323b09ac62d692093d8c0f5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81287265"
---
# <a name="sqlsetscrolloptions-function"></a>SQLSetScrollOptions, fonction
**Conformité**  
 Version introduite: ODBC 1.0 Standards Compliance: Deprecated  
  
 **Résumé**  
 Dans ODBC *3.x*, la fonction ODBC 2.0 **SQLSetScrollOptions** a été remplacée par des appels à **SQLGetInfo** et **SQLSetStmtAttr**.  
  
> [!NOTE]
>  Pour plus d’informations sur ce que le Gestionnaire de conducteur cartographie cette fonction à quand une application ODBC *2.x* travaille avec un pilote ODBC *3.x,* voir [Mapping Deprecated Functions](../../../odbc/reference/appendixes/mapping-deprecated-functions.md) in Appendix G: Driver Guidelines for Backward Compatibility.  
> 
> [!NOTE]
>  Lorsque le gestionnaire de chauffeur cartes **SQLSetScrollOptions** pour une application de travail avec un pilote ODBC *3.x* qui ne prend pas en charge **SQLSetScrollOptions**, le gestionnaire de conducteur définit l’option de déclaration SQL_ROWSET_SIZE, et non l’attribut de déclaration SQL_ATTR_ROW_ARRAY_SIZE, à l’argument *RowsetSize* dans **SQLSetScrollOption**. Par conséquent, **SQLSetScrollOptions** ne peut pas être utilisé par une application lorsqu’il s’agit d’aller chercher plusieurs rangées par un appel à **SQLFetch** ou **SQLFetchScroll**. Il ne peut être utilisé que lorsque vous allez chercher plusieurs rangées par un appel à **SQLExtendedFetch**.  
  
## <a name="remarks"></a>Notes  
 Si votre application s’exécute sur un système d’exploitation 64 bits, consultez [ODBC 64-Bit Information](../../../odbc/reference/odbc-64-bit-information.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
