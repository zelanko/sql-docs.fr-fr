---
description: Méthode supportsGetGeneratedKeys (SQLServerDatabaseMetaData)
title: Méthode supportsGetGeneratedKeys (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsGetGeneratedKeys
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4f0e4659-14e7-4743-aed8-1768ee2b29dd
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c27704022f1da09fdca6ec5f9697abed8bf3e3cf
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88467031"
---
# <a name="supportsgetgeneratedkeys-method-sqlserverdatabasemetadata"></a>Méthode supportsGetGeneratedKeys (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère les informations déterminant si les clés générées automatiquement peuvent être récupérées après l'exécution d'une instruction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean supportsGetGeneratedKeys()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **true** en cas de prise en charge. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode supportsGetGeneratedKeys est spécifiée par la méthode supportsGetGeneratedKeys de l’interface java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
