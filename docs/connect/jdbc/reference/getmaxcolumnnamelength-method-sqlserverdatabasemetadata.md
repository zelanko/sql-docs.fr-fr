---
description: Méthode getMaxColumnNameLength (SQLServerDatabaseMetaData)
title: Méthode getMaxColumnNameLength (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getMaxColumnNameLength
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 67fb5407-55b9-48b6-87f3-112700f304ba
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f014ef391062da5289353e44b56e25f598f19053
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88435641"
---
# <a name="getmaxcolumnnamelength-method-sqlserverdatabasemetadata"></a>Méthode getMaxColumnNameLength (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère le nombre maximal de caractères autorisé par cette base de données pour un nom de colonne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int getMaxColumnNameLength()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **int** indiquant le nombre maximal de caractères autorisé.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getMaxColumnNameLength est spécifiée par la méthode getMaxColumnNameLength de l’interface java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
