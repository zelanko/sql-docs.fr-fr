---
title: Méthode supportsExpressionsInOrderBy (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsExpressionsInOrderBy
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 858f3c02-4531-4775-97e9-a03b316bdaba
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 249e10054a537ed26006551a6f8b09b05f741ac3
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47721007"
---
# <a name="supportsexpressionsinorderby-method-sqlserverdatabasemetadata"></a>Méthode supportsExpressionsInOrderBy (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère les informations déterminant si cette base de données prend en charge les expressions dans les listes ORDER BY.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean supportsExpressionsInOrderBy()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si pris en charge. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode supportsExpressionsInOrderBy est spécifiée par la méthode supportsExpressionsInOrderBy dans l’interface java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
