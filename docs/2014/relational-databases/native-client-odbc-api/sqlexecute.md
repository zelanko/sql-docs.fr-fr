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
author: rothja
ms.author: jroth
ms.openlocfilehash: 514436c65ef103cafae2189a03b560255b447eda
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85022533"
---
# <a name="sqlexecute"></a>SQLExecute
  Si l’attribut d’instruction SQL_SOPT_SS_PARAM_FOCUS n’a pas la valeur 0, SQLExecute retourne SQL_ERROR et génère un enregistrement de diagnostic avec SQLSTATE = HY024 et le message « valeur d’attribut non valide, SQL_SOPT_SS_PARAM_FOCUS (doit être égal à zéro au moment de l’exécution) ». Pour plus d'informations sur SQL_SOPT_SS_PARAM_FOCUS, consultez [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
## <a name="remarks"></a>Remarques  
 Pour plus d’informations sur les paramètres table, consultez [paramètres table &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=80708)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  
