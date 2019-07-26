---
title: Méthode isWritable (SQLServerResultSetMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSetMetaData.isWritable
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 50846aa8-e4e5-4fc3-a638-0e5fa8b597be
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8d5a22e4fa9a3bd27da1862b0157324e3fbe9098
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67977011"
---
# <a name="iswritable-method-sqlserverresultsetmetadata"></a>Méthode isWritable (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indique si une écriture dans la colonne désignée peut réussir.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean isWritable(int column)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *column*  
  
 **Entier** qui indique l’index de colonne.  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si les écritures échouent sur la colonne. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode isWritable est spécifiée par la méthode isWritable dans l’interface java. Sql. ResultSetMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerResultSetMetaData, méthodes](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [SQLServerResultSetMetaData, membres](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [SQLServerResultSetMetaData, classe](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
