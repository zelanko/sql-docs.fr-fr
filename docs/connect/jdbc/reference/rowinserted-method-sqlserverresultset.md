---
title: "rowInserted (méthode) (SQLServerResultSet) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerResultSet.rowInserted
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: e7c10372-0be8-4baa-87f7-ed6b66003357
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: a4431409cc168ad07086516e5234f2a975916596
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="rowinserted-method-sqlserverresultset"></a>rowInserted (méthode) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère les informations déterminant si la ligne actuelle a eu une insertion.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean rowInserted()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si une ligne a eu une insertion et les insertions sont détectées. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode rowUpdated est spécifiée par la méthode rowUpdated dans l’interface java.sql.ResultSet.  
  
 La valeur retournée dépend de si cela [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objet peut détecter des insertions visibles.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]ne détecte pas les lignes insérées pour n’importe quel type de curseur.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
