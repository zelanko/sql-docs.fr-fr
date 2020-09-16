---
description: Méthode getTableName (SQLServerResultSetMetaData)
title: Méthode getTableName (SQLServerResultSetMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSetMetaData.getTableName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9a077b50-cc5a-4301-9398-49ea68544e89
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 27002f0e425edafcd04bc0c73463d581fcd9eb39
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88434221"
---
# <a name="gettablename-method-sqlserverresultsetmetadata"></a>Méthode getTableName (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Obtient le nom de table de la colonne désignée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.String getTableName(int column)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *column*  
  
 **int** indiquant l’index de la colonne.  
  
## <a name="return-value"></a>Valeur de retour  
 **Chaîne** qui contient le nom de la table.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getTableName est spécifiée par la méthode getTableName de l'interface java.sql.ResultSetMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerResultSetMetaData, méthodes](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [SQLServerResultSetMetaData, membres](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [SQLServerResultSetMetaData, classe](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
