---
description: Méthode executeBatch (SQLServerPreparedStatement)
title: executeBatch, méthode (SQLServerPreparedStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.executeBatch
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8418167e-cbd2-464d-b118-73cdd76080ed
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 53d0881e5e948d857c5a5941977f0945ea461794
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88437731"
---
# <a name="executebatch-method-sqlserverpreparedstatement"></a>Méthode executeBatch (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Envoie un lot de commandes à exécuter à la base de données. En cas d'exécution correcte de toutes les commandes, un tableau des nombres de mises à jour est retourné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int[] executeBatch()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Tableau d'entiers qui contient les nombres de mises à jour.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
 java.sql.BatchUpdateException  
  
## <a name="remarks"></a>Notes  
 Cette méthode executeBatch est spécifiée par la méthode executeBatch de l’interface java.sql.Statement.  
    
 Cette méthode remplace [SQLServerStatement.executeBatch](../../../connect/jdbc/reference/executebatch-method-sqlserverstatement.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerPreparedStatement, membres](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [Classe SQLServerPreparedStatement](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
