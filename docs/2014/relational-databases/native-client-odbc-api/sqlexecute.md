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
ms.openlocfilehash: fab0ac676e4d0fc1b9d74c4aa9d1e472b8316a7e
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48095292"
---
# <a name="sqlexecute"></a>SQLExecute
  Si l’attribut d’instruction que sql_sopt_ss_param_focus n’est pas définie sur 0, SQLExecute retourne SQL_ERROR et génère un enregistrement de diagnostic avec SQLSTATE = HY024 et le message « valeur d’attribut non valide, SQL_SOPT_SS_PARAM_FOCUS (doit être pas égale à zéro au moment de l’exécution) ». Pour plus d’informations sur SQL_SOPT_SS_PARAM_FOCUS, consultez [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur les paramètres table, consultez [paramètres table &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLExecute](http://go.microsoft.com/fwlink/?LinkId=80708)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  
