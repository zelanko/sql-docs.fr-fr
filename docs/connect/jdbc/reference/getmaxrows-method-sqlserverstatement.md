---
description: getMaxRows, méthode (SQLServerStatement)
title: Méthode getMaxRows (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getMaxRows
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6aece4e5-027d-434e-a8cf-a67c0484f189
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c4fe0ef1e178b3462c51f7ab2eb9b2c85eef4dc0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88435531"
---
# <a name="getmaxrows-method-sqlserverstatement"></a>getMaxRows, méthode (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère le nombre maximal de lignes que peut contenir un objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) produit par cet objet [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final int getMaxRows()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **int** indiquant le nombre maximal de lignes, ou 0 s’il n’y a pas de limite.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getMaxRows est spécifiée par la méthode getMaxRows de l’interface java.sql.Statement.  
  
 Cette méthode getMaxRows retourne toujours 0 pour les curseurs dynamiques à défilement.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerStatement, membres](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
