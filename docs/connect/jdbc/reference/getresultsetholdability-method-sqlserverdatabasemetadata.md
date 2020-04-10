---
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
ms.openlocfilehash: 137f2388f940bfbf17038af3288dea6c8b944e26
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80921860"
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
  
  
