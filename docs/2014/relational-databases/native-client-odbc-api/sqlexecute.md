---
title: SQLExecute | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLExecute function
ms.assetid: 4d7db8b6-611f-4fe4-be85-2a407059de45
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3ad659cfb929ac5a489b069db0b6a5f2b8abdae7
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "63067495"
---
# <a name="sqlexecute"></a>SQLExecute
  Si l’attribut d’instruction SQL_SOPT_SS_PARAM_FOCUS n’a pas la valeur 0, SQLExecute retourne SQL_ERROR et génère un enregistrement de diagnostic avec SQLSTATE = HY024 et le message « valeur d’attribut non valide, SQL_SOPT_SS_PARAM_FOCUS (doit être égal à zéro au moment de l’exécution) ». Pour plus d'informations sur SQL_SOPT_SS_PARAM_FOCUS, consultez [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur les paramètres table, consultez [paramètres table &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=80708)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  
