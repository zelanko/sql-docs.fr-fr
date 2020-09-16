---
description: Méthode getResultSetHoldability (SQLServerDatabaseMetaData)
title: Méthode getResultSetHoldability (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData,getResultSetHoldability
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f0bd6283-83ab-4a0a-b825-ec4cdccf03e1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d302a290ce0dcc88d6d27c2b3e01570cf596633e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88434841"
---
# <a name="getresultsetholdability-method-sqlserverdatabasemetadata"></a>Méthode getResultSetHoldability (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la fonctionnalité par défaut de mise en attente des jeux de résultats pour cette base de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int getResultSetHoldability()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **int** indiquant la mise en attente par défaut.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getResultSetHoldability est spécifiée par la méthode getResultSetHoldability de l’interface java.sql.DatabaseMetaData.  
  
 Lors de l’utilisation du [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] avec une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], cette méthode retourne 1, ce qui équivaut à la constante ResultSet.HOLD_CURSORS_OVER_COMMIT.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
