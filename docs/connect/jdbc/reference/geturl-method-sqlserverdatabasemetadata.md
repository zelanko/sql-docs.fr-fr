---
description: Méthode getURL (SQLServerDatabaseMetaData)
title: Méthode getURL (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getURL
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: fcb66851-db5f-4ae8-b728-d129480b6f42
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7371c5aa585c7ffc9ec434e8c0dbc5ae6ecc4d89
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88433871"
---
# <a name="geturl-method-sqlserverdatabasemetadata"></a>Méthode getURL (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère l'URL pour cette base de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.String getURL()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **Chaîne** qui contient l’URL.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getURL est spécifiée par la méthode getURL dans l’interface java.sql.DatabaseMetaData.  
  
 Lors de l’utilisation du [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] avec une base de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], cette méthode retourne une valeur **chaîne** qui contient les informations suivantes :  
  
-   Valeur URL de « jdbc:sqlserver:// »  
  
-   Propriétés de connexion facultatives, telles que **serverName**, **instanceName**, et **portNumber**  
  
-   Autres propriétés de connexion définies par l’utilisateur et toutes les propriétés de connexion avec des valeurs par défaut de pilote non vides et non Null, à l’exception de **userName**, **password** et **integratedSecurity**.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
