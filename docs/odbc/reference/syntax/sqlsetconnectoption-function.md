---
title: Fonction SQLSetConnectOption | Documents Microsoft
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
- SQLSetConnectOption
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLSetConnectOption
helpviewer_keywords:
- SQLSetConnectOption function [ODBC]
ms.assetid: 8cd2c2a2-25c8-4aff-951c-b593bbfc90ad
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b5499852e3574c597e3a424347b22021d0887ca9
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetconnectoption-function"></a>Fonction SQLSetConnectOption
**Mise en conformité**  
 Version introduite : Conformité de normes 1.0 ODBC : déconseillé  
  
 **Résumé**  
 Dans ODBC 3*.x*, la fonction ODBC 2.0 **SQLSetConnectOption** a été remplacé par **SQLSetConnectAttr**. Pour plus d’informations, consultez [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
> [!NOTE]  
>  Pour plus d’informations sur ce que le Gestionnaire de pilotes mappe cette fonction pour lorsqu’un ODBC 2*.x* application fonctionne avec un ODBC 3*.x* pilote, consultez [mappage des fonctions déconseillées](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)».  
  
## <a name="remarks"></a>Notes  
 Consultez [informations ODBC 64 bits](../../../odbc/reference/odbc-64-bit-information.md), si votre application s’exécutera sur un système d’exploitation de 64 bits.  
  
> [!NOTE]  
>  Ne prend pas en charge l’attribut SQL_ASYNC_DBC_FUNCTION_ENABLE introduite dans ODBC 3.8 **SQLSetConnectOption**. Les applications qui utilisent l’opération asynchrone sur le handle de connexion doivent utiliser **SQLSetConnectAttr**.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
