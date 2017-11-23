---
title: "Méthode getURL (SQLServerDataSource) | Documents Microsoft"
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
apiname: SQLServerDataSource.getURL
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: dd0d5d2c-91fe-4b0f-a162-69d898ba176e
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 5859a931b0319b486870427acf15bcddd30ddaea
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="geturl-method-sqlserverdatasource"></a>Méthode getURL (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne l'URL utilisée pour la connexion à la source de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.String getURL()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 A **chaîne** qui contient l’URL.  
  
## <a name="remarks"></a>Notes  
 Pour des raisons de sécurité, vous n’incluez pas le mot de passe dans l’URL fournie à la [setURL](../../../connect/jdbc/reference/seturl-method-sqlserverdatasource.md) (méthode). En effet, les serveurs d'applications Java tiers affichent très souvent la valeur définie pour la propriété URL dans l'interface utilisateur de configuration de la source de données. Utilisez plutôt le [setPassword](../../../connect/jdbc/reference/setpassword-method-sqlserverdatasource.md) méthode pour définir la valeur de mot de passe. Les serveurs d'applications Java n'affichent pas de mot de passe défini dans leur source de données à l'intérieur de l'interface utilisateur de configuration.  
  
> [!NOTE]  
>  Si la méthode setURL n’est pas appelée avant d’appeler la méthode getURL, getURL retourne la valeur par défaut « SQLServer : / / ».  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
