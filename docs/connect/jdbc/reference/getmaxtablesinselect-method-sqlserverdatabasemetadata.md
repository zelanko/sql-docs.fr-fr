---
title: Méthode getMaxTablesInSelect (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getMaxTablesInSelect
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f5291217-2a0c-4daa-9e39-9f348fc911f7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d125e9dad6d5c6f82ff177abdaced9d784295c11
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67981923"
---
# <a name="getmaxtablesinselect-method-sqlserverdatabasemetadata"></a>Méthode getMaxTablesInSelect (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère le nombre maximal de tables autorisé par cette base de données dans une instruction SELECT.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int getMaxTablesInSelect()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 **Entier** qui indique le nombre maximal de tables autorisées.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getMaxTablesInSelect, est spécifiée par la méthode getMaxTablesInSelect, dans l’interface java. Sql. DatabaseMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
