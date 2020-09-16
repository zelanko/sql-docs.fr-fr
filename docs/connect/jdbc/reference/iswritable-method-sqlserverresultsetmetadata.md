---
description: Méthode isWritable (SQLServerResultSetMetaData)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 56f7d240f82209c46414e40d1c7b6518f198239e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88433271"
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
  
 **int** indiquant l’index de la colonne.  
  
## <a name="return-value"></a>Valeur de retour  
 **true** si les écritures réussissent sur la colonne. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode isWritable est spécifiée par la méthode isWritable de l'interface java.sql.ResultSetMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerResultSetMetaData, méthodes](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [SQLServerResultSetMetaData, membres](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [SQLServerResultSetMetaData, classe](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
