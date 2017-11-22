---
title: "Méthode setUser (SQLServerDataSource) | Documents Microsoft"
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
apiname: SQLServerDataSource.setUser
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: d2ea7906-2d10-438d-aa51-f576eea923c7
caps.latest.revision: "9"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 65cabdc5522527af282d48570cb0ca41887c3ea5
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="setuser-method-sqlserverdatasource"></a>Méthode setUser (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le nom d'utilisateur utilisé pour la connexion à la source de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setUser(java.lang.String user)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *utilisateur*  
  
 A **chaîne** qui contient le nom d’utilisateur.  
  
## <a name="remarks"></a>Notes  
 La méthode setUser définit le nom d’utilisateur qui permet de se connecter à [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]. Si la valeur de nom d’utilisateur n’est pas définie, la [getUser](../../../connect/jdbc/reference/getuser-method-sqlserverdatasource.md) méthode retourne la valeur par défaut null.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
