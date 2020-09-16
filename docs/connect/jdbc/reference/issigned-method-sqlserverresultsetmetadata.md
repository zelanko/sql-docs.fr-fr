---
description: Méthode isSigned (SQLServerResultSetMetaData)
title: Méthode isSigned (SQLServerResultSetMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSetMetaData.isSigned
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 1d16672f-1515-4255-8b20-e7911c999f60
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9639b4511a65d563a1ba7168aadbe80ee363b8b9
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88433381"
---
# <a name="issigned-method-sqlserverresultsetmetadata"></a>Méthode isSigned (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indique si les valeurs de la colonne désignée sont des nombres signés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean isSigned(int column)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *column*  
  
 **int** indiquant l’index de la colonne.  
  
## <a name="return-value"></a>Valeur de retour  
 **true** si la colonne contient des nombres signés. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode isSigned est spécifiée par la méthode isSigned de l’interface java.sql.ResultSetMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerResultSetMetaData, méthodes](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [SQLServerResultSetMetaData, membres](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [SQLServerResultSetMetaData, classe](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
