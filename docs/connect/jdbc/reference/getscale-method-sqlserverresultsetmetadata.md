---
title: "Méthode getScale (SQLServerResultSetMetaData) | Documents Microsoft"
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
apiname: SQLServerResultSetMetaData.getScale
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: fe29aa5f-4cc5-413f-8bbd-a58064993d87
caps.latest.revision: "12"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 735f2aa42382009aae985adc10e6ad1affe2d04d
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="getscale-method-sqlserverresultsetmetadata"></a>Méthode getScale (SQLServerResultSetMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Obtient le nombre de chiffres à droite de la virgule décimale pour la colonne désignée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int getScale(int column)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *colonne*  
  
 Un **int** qui indique l’index de colonne.  
  
## <a name="return-value"></a>Valeur retournée  
 Un **int** qui indique l’échelle de la colonne.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getScale est spécifiée par la méthode getScale dans l’interface java.sql.ResultSetMetaData.  
  
 [!INCLUDE[msCoName](../../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] Version 3.0 du pilote JDBC comporte des modifications de comportement dans la colonne DECIMAL_DIGITS. Consultez [SQLServerDatabaseMetaData.getColumns](../../../connect/jdbc/reference/getcolumns-method-sqlserverdatabasemetadata.md) pour plus d’informations.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerResultSetMetaData](../../../connect/jdbc/reference/sqlserverresultsetmetadata-members.md)   
 [SQLServerResultSetMetaData, classe](../../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md)  
  
  
