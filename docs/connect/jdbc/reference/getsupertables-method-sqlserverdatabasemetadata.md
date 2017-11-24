---
title: "Méthode getSuperTables (SQLServerDatabaseMetaData) | Documents Microsoft"
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
apiname: SQLServerDatabaseMetaData.getSuperTables
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 085461de-367b-4832-88aa-010813d2bc41
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: fdda31ad9072b5c4353038011cf700633125997e
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="getsupertables-method-sqlserverdatabasemetadata"></a>Méthode getSuperTables (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère une description des hiérarchies de table définies dans un schéma particulier de cette base de données.  
  
> [!NOTE]  
>  Cette méthode n’est pas actuellement pris en charge avec le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]. Lorsqu'elle est utilisée, cette méthode retourne toujours un jeu de résultats vide.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.ResultSet getSuperTables(java.lang.String catalog,  
                                         java.lang.String schemaPattern,  
                                         java.lang.String tableNamePattern)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *catalogue*  
  
 A **chaîne** qui contient le nom du catalogue.  
  
 *schemaPattern*  
  
 A **chaîne** qui contient le modèle de nom de schéma.  
  
 *tableNamePattern*  
  
 A **chaîne** qui contient le modèle de nom de table.  
  
## <a name="return-value"></a>Valeur retournée  
 A [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objet.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getSuperTables est spécifiée par la méthode getSuperTables dans l’interface java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membres de SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
