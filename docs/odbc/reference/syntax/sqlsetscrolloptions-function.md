---
title: SQLSetScrollOptions fonction) | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81287265"
---
# <a name="sqlsetscrolloptions-function"></a>SQLSetScrollOptions, fonction
**Conformité**  
 Version introduite : conformité des normes ODBC 1,0 : déconseillé  
  
 **Résumé**  
 Dans ODBC *3. x*, la fonction ODBC 2,0 **SQLSetScrollOptions** a été remplacée par des appels à **SQLGetInfo** et **SQLSetStmtAttr**.  
  
> [!NOTE]
>  Pour plus d’informations sur le mappage de cette fonction par le gestionnaire de pilotes lorsqu’une application ODBC *2. x* utilise un pilote ODBC *3. x* , consultez [mappage des fonctions déconseillées](../../../odbc/reference/appendixes/mapping-deprecated-functions.md) dans l’annexe G : instructions relatives aux pilotes pour la compatibilité descendante.  
> 
> [!NOTE]
>  Quand le gestionnaire de pilotes mappe **SQLSetScrollOptions** pour une application qui utilise un pilote ODBC *3. x* qui ne prend pas en charge **SQLSetScrollOptions**, le gestionnaire de pilotes définit l’option d’instruction SQL_ROWSET_SIZE, et non l’attribut d’instruction SQL_ATTR_ROW_ARRAY_SIZE, sur l’argument *RowsetSize* dans **SQLSetScrollOption**. Par conséquent, **SQLSetScrollOptions** ne peut pas être utilisé par une application lors de l’extraction de plusieurs lignes par un appel à **SQLFetch** ou **SQLFetchScroll**. Il peut être utilisé uniquement lors de l’extraction de plusieurs lignes par un appel à **SQLExtendedFetch**.  
  
## <a name="remarks"></a>Notes  
 Si votre application s’exécute sur un système d’exploitation 64 bits, consultez [informations ODBC 64](../../../odbc/reference/odbc-64-bit-information.md)bits.  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
