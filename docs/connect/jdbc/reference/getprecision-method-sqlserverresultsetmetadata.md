---
title: "Méthode getPrecision (SQLServerResultSetMetaData) | Documents Microsoft"
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
apiname: SQLServerResultSetMetaData.getPrecision
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: de46c96e-6ad6-4946-883e-807123658500
caps.latest.revision: "7"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ca52ca740162aee4072e4d389df72b613f765892
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="getprecision-method-sqlserverresultsetmetadata"></a>Méthode getPrecision (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Obtenir le numéro de la colonne désignée de chiffres décimaux.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int getPrecision(int column)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *colonne*  
  
 Un **int** qui indique l’index de colonne.  
  
## <a name="return-value"></a>Valeur retournée  
 Un **int** qui indique la précision de la colonne.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getPrecision est spécifiée par la méthode getPrecision dans l’interface java.sql.ResultSetMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-methods.md)   
 [Membres de SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [SQLServerResultSetMetaData, classe](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
