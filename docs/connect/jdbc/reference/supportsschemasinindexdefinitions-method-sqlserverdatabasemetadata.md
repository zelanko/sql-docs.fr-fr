---
title: Méthode supportsSchemasInIndexDefinitions | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsSchemasInIndexDefinitions
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 55ce9e4f-6e3f-482a-93a5-b9ae1b91d7a3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b472c7df1b0bade87dad979421636cb8a386c3bd
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67968901"
---
# <a name="supportsschemasinindexdefinitions-method-sqlserverdatabasemetadata"></a>Méthode supportsSchemasInIndexDefinitions (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère les informations déterminant si un nom de schéma peut être utilisé dans une instruction de définition d'index.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean supportsSchemasInIndexDefinitions()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si pris en charge. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode supportsSchemasInIndexDefinitions est spécifiée par la méthode supportsSchemasInIndexDefinitions dans l’interface java. Sql. DatabaseMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
