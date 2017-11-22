---
title: "rowDeleted (méthode) (SQLServerResultSet) | Documents Microsoft"
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
apiname: SQLServerResultSet.rowDeleted
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 9c6db315-e614-4604-b020-41af6a214cc1
caps.latest.revision: "8"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1e4615318e2ca36d7524d25b0c5fcbf003711ee7
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="rowdeleted-method-sqlserverresultset"></a>rowDeleted (méthode) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère les informations déterminant si une ligne a été supprimée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean rowDeleted()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si une ligne a été supprimée et les suppressions sont détectées. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode rowDeleted est spécifiée par la méthode rowDeleted dans l’interface java.sql.ResultSet.  
  
 Une ligne supprimée peut laisser un trou visible dans un jeu de résultats. Cette méthode peut être utilisée pour détecter des trous dans un jeu de résultats. La valeur retournée dépend de si cela [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objet peut détecter les suppressions.  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]détecte les lignes supprimées pour tous les types de curseur modifiable, bien que la détection soit temporaire pour les curseurs avant et dynamiques.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
