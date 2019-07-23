---
title: Méthode supportsSavepoints, (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsSavepoints
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: cd2418c9-e95d-4820-82bd-944287387b60
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a4359c68d2376d933e919a03dcd230a9df9ea307
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67968920"
---
# <a name="supportssavepoints-method-sqlserverdatabasemetadata"></a>Méthode supportsSavepoints (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère les informations déterminant si cette base de données prend en charge les points de sauvegarde.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean supportsSavepoints()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si pris en charge. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode supportsSavepoints, est spécifiée par la méthode supportsSavepoints, dans l’interface java. Sql. DatabaseMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
