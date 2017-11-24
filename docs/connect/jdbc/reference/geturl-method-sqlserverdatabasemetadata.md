---
title: "Méthode getURL (SQLServerDatabaseMetaData) | Documents Microsoft"
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
apiname: SQLServerDatabaseMetaData.getURL
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: fcb66851-db5f-4ae8-b728-d129480b6f42
caps.latest.revision: "20"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: cbc569dbd45ede9429b6299e2f37d7f7a5cb269c
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="geturl-method-sqlserverdatabasemetadata"></a>Méthode getURL (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère l'URL pour cette base de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.String getURL()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 A **chaîne** qui contient l’URL.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getURL est spécifiée par la méthode getURL dans l’interface java.sql.DatabaseMetaData.  
  
 Lorsque vous utilisez la [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] avec un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] de base de données, cette méthode retourne un **chaîne** valeur qui contient les informations suivantes :  
  
-   Valeur URL de « jdbc:sqlserver:// »  
  
-   Propriétés de connexion facultatifs, tels que **nom_serveur**, **instanceName**, et **numéro_port**  
  
-   Autres propriétés de connexion défini par l’utilisateur et toutes les connexions propriétés avec le pilote non vide ou non null les valeurs par défaut, à l’exception **nom d’utilisateur**, **mot de passe**, et **integratedSecurity**.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membres de SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
