---
description: getUpdateCount, méthode (SQLServerStatement)
title: Méthode getUpdateCount (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getUpdateCount
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e9570228-4500-44b6-b2f1-84ac050b5112
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 19a4cfc7b9957d8ba4392477e6dcd3732f10bd7c
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88433901"
---
# <a name="getupdatecount-method-sqlserverstatement"></a>getUpdateCount, méthode (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère le résultat actuel en tant que nombre de mises à jour.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final int getUpdateCount()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **int** contenant le nombre de mises à jour. Si le résultat retourné est un objet de jeu de résultats ou s'il n'y a plus de résultat, -1 est retourné.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getUpdateCount est spécifiée par la méthode getUpdateCount de l’interface java.sql.Statement.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerStatement, membres](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
