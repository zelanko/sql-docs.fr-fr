---
title: SQLSetConnectOption, fonction | Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b429e499cccaad553236b4ebee78374c69c7c4dd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68093011"
---
# <a name="sqlsetconnectoption-function"></a>SQLSetConnectOption, fonction
**Conformité**  
 Version introduite : Conformité aux normes 1.0 ODBC : Déconseillé  
  
 **Résumé**  
 Dans ODBC 3 *.x*, la fonction ODBC 2.0 **SQLSetConnectOption** a été remplacé par **SQLSetConnectAttr**. Pour plus d’informations, consultez [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md).  
  
> [!NOTE]
>  Pour plus d’informations sur ce que le Gestionnaire de pilotes mappe cette fonction lorsqu’un ODBC 2 *.x* application fonctionne avec un ODBC 3 *.x* pilote, consultez [mappage de fonctions déconseillées](../../../odbc/reference/appendixes/mapping-deprecated-functions.md)".  
  
## <a name="remarks"></a>Notes  
 Consultez [informations sur ODBC 64 bits](../../../odbc/reference/odbc-64-bit-information.md), si votre application s’exécutera sur un système d’exploitation 64 bits.  
  
> [!NOTE]  
>  Ne prend pas en charge l’attribut SQL_ASYNC_DBC_FUNCTION_ENABLE introduite dans ODBC 3.8 **SQLSetConnectOption**. Applications qui utilisent l’opération asynchrone sur le handle de connexion doivent utiliser **SQLSetConnectAttr**.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence de l’API ODBC](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [Fichiers d’en-tête ODBC](../../../odbc/reference/install/odbc-header-files.md)
