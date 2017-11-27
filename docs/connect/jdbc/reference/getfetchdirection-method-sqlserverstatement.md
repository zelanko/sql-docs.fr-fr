---
title: "Méthode getFetchDirection (SQLServerStatement) | Documents Microsoft"
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
apiname: SQLServerStatement.getFetchDirection
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: ceb4ae68-decc-46d3-83f1-0bbd23aaf58c
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ff5ec8aa9e65c3c2881bef50f25dd8be726d8908
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="getfetchdirection-method-sqlserverstatement"></a>Méthode getFetchDirection (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la direction de l’extraction de lignes à partir des tables de base de données qui est la valeur par défaut pour les jeux de résultats qui sont générés à partir de ce [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) objet.  
  
> [!NOTE]  
>  Cette méthode n’est pas implémentée actuellement par le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]. Par conséquent, elle retourne toujours FETCH_UNKNOWN.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final int getFetchDirection()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Un **int** qui indique la direction d’extraction qui est spécifiée par le [setFetchDirection](../../../connect/jdbc/reference/setfetchdirection-method-sqlserverstatement.md) (méthode).  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getFetchDirection est spécifiée par la méthode getFetchDirection dans l’interface java.sql.Statement.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
