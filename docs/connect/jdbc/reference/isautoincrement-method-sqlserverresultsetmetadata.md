---
title: Méthode isAutoIncrement (SQLServerResultSetMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSetMetaData.isAutoIncrement
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 028b8d61-9557-4c9f-b732-29e87a962de8
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 27238772e437bc6bd5f8b33bed7e89dd0c294a3a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67977822"
---
# <a name="isautoincrement-method-sqlserverresultsetmetadata"></a>Méthode isAutoIncrement (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indique si la colonne désignée est numérotée automatiquement, la plaçant ainsi en lecture seule.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean isAutoIncrement(int column)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *column*  
  
 **Entier** qui indique l’index de colonne.  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si la colonne est numérotée automatiquement. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode isAutoIncrement est spécifiée par la méthode isAutoIncrement dans l’interface java. Sql. ResultSetMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerResultSetMetaData, méthodes](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [SQLServerResultSetMetaData, membres](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [SQLServerResultSetMetaData, classe](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
