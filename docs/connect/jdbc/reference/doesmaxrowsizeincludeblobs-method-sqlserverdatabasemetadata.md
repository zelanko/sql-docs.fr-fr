---
title: Méthode doesMaxRowSizeIncludeBlobs (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.doesMaxRowSizeIncludeBlobs
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 0c90a7a7-5a59-4858-bb26-3e725d8611d7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7b13eb0333a943444a45c578c2d10a5a7394b5d7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67955114"
---
# <a name="doesmaxrowsizeincludeblobs-method-sqlserverdatabasemetadata"></a>Méthode doesMaxRowSizeIncludeBlobs (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère les informations indiquant si la valeur retournée de la méthode [getMaxRowSize](../../../connect/jdbc/reference/getmaxrowsize-method-sqlserverdatabasemetadata.md) inclut les types de données SQL LONGVARCHAR et LONGVARBINARY.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean doesMaxRowSizeIncludeBlobs()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si la valeur de retour comprend les types de données. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode doesMoxRowSizeIncludeBlobs est spécifiée par la méthode doesMoxRowSizeIncludeBlobs dans l’interface java. Sql. DatabaseMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
