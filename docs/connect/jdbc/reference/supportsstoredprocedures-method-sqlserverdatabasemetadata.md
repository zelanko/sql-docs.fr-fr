---
title: Méthode supportsStoredProcedures | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsStoredProcedures
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 776ff53a-8bf3-4864-a7b7-170fdef1a87b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: dd3c71aa058534342ddd70fdf1ae5256fb75e708
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67968761"
---
# <a name="supportsstoredprocedures-method-sqlserverdatabasemetadata"></a>Méthode supportsStoredProcedures (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère les informations déterminant si cette base de données prend en charge les appels de procédures stockées qui utilisent la syntaxe d'échappement de procédure stockée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean supportsStoredProcedures()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si pris en charge. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode supportsStoredProcedures est spécifiée par la méthode supportsStoredProcedures dans l’interface java. Sql. DatabaseMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
