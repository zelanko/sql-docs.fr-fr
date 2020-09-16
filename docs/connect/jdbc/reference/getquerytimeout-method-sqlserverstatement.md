---
description: Méthode getQueryTimeout (SQLServerStatement)
title: Méthode getQueryTimeout (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getQueryTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8dff954f-b458-4fa6-abe6-be62ff75e2b9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: efc25cfa3b1a43f8c818e66007245853d8159e24
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88434911"
---
# <a name="getquerytimeout-method-sqlserverstatement"></a>Méthode getQueryTimeout (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère le nombre de secondes pendant lesquelles [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] attend que cet objet [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) s’exécute.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final int getQueryTimeout()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **int** indiquant le nombre de secondes d’attente du pilote JDBC, ou 0 s’il n’y a pas de limite.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getQueryTimeout est spécifiée par la méthode getQueryTimeout de l’interface java.sql.Statement.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerStatement, membres](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
