---
title: SQLExecDirect | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLExecDirect function
ms.assetid: e7c2a5b5-83f4-4c72-9aca-7b9fb4748b11
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 36a5d580b6edb04f51d2fcf77dcc8ff0c8ba042f
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82706147"
---
# <a name="sqlexecdirect"></a>SQLExecDirect
  Si l’attribut d’instruction SQL_SOPT_SS_PARAM_FOCUS n’a pas la valeur 0, SQLExecDirect retourne SQL_ERROR et génère un enregistrement de diagnostic avec SQLSTATE = HY024 et le message « valeur d’attribut non valide, SQL_SOPT_SS_PARAM_FOCUS (doit être égal à zéro au moment de l’exécution) ». Pour plus d'informations sur SQL_SOPT_SS_PARAM_FOCUS, consultez [SQLSetStmtAttr](sqlsetstmtattr.md).  
  
 Pour plus d’informations sur les paramètres table, consultez [paramètres table &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=80709)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  
