---
description: Méthode getSystemFunctions (SQLServerDatabaseMetaData)
title: Méthode getSystemFunctions (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getSystemFunctions
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 6d390ec5-9ee2-49c4-b661-a93b55691dd1
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a15a0a39c9da932e132e6b765e1ea3daf7f6519e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88434231"
---
# <a name="getsystemfunctions-method-sqlserverdatabasemetadata"></a>Méthode getSystemFunctions (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère une liste séparée par des virgules des fonctions système disponibles avec cette base de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.String getSystemFunctions()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **Chaîne** contenant la liste des fonctions système.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getSystemFunctions est spécifiée par la méthode getSystemFunctions de l’interface java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
