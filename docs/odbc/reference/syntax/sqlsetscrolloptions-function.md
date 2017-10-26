---
title: Fonction de SQLSetScrollOptions | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLSetScrollOptions
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetScrollOptions
helpviewer_keywords:
- SQLSetScrollOptions function [ODBC]
ms.assetid: 2a825ba7-7942-4c23-bcdb-c80dc12f8c86
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 432fbea7fb864b0a42a000eb46df6c2642b7c28b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetscrolloptions-function"></a>SQLSetScrollOptions (fonction)
**Mise en conformité**  
 Version introduite : Conformité de normes 1.0 ODBC : déconseillé  
  
 **Résumé**  
 Dans ODBC 3*.x*, la fonction ODBC 2.0 **SQLSetScrollOptions** a été remplacée par les appels à **SQLGetInfo** et **SQLSetStmtAttr**.  
  
> [!NOTE]  
>  Pour plus d’informations sur ce que le Gestionnaire de pilotes mappe cette fonction pour lorsqu’un ODBC 2*.x* application fonctionne avec un ODBC 3*.x* pilote, consultez [mappage des fonctions déconseillées](../../../odbc/reference/appendixes/mapping-deprecated-functions.md) dans l’annexe g : pilote recommandations pour la compatibilité descendante.  
  
> [!NOTE]  
>  Lorsque le Gestionnaire de pilotes mappe **SQLSetScrollOptions** pour une application utilisant une ODBC 3*.x* pilote qui ne prend pas en charge **SQLSetScrollOptions**, le Gestionnaire de pilotes définit l’option d’instruction SQL_ROWSET_SIZE, pas l’attribut d’instruction SQL_ATTR_ROW_ARRAY_SIZE, à la *la RowsetSize* argument dans **SQLSetScrollOption**. Par conséquent, **SQLSetScrollOptions** ne peut pas être utilisé par une application lors de l’extraction de plusieurs lignes par un appel à **SQLFetch** ou **SQLFetchScroll**. Il peut être utilisé uniquement lors de l’extraction de plusieurs lignes par un appel à **SQLExtendedFetch**.  
  
## <a name="remarks"></a>Notes  
 Si votre application s’exécutera sur un système d’exploitation de 64 bits, consultez [informations ODBC 64 bits](../../../odbc/reference/odbc-64-bit-information.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)

