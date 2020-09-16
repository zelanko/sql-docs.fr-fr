---
description: Méthode isReadOnly (SQLServerDatabaseMetaData)
title: Méthode isReadOnly (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.isReadOnly
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: d1569e03-b7bd-486a-af0b-d3f108f712dc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4ba16708b03651b7db9f0587c2d7bca2fb9496fb
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88433431"
---
# <a name="isreadonly-method-sqlserverdatabasemetadata"></a>Méthode isReadOnly (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère les informations déterminant si cette base de données est en mode lecture seule.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean isReadOnly()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **true** si la base de données est en mode lecture seule. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode isReadOnly est spécifiée par la méthode isReadOnly de l’interface java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
