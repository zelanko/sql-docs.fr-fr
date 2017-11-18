---
title: "Méthode getServerName (SQLServerDataSource) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDataSource.getServerName
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3004ed22-5d69-4dd0-8761-d39f0b7dde13
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2f7c77c52a62465eea584e3fa695810a65ffc202
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="getservername-method-sqlserverdatasource"></a>Méthode getServerName (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne le nom de la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] instance.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.String getServerName()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 A **chaîne** qui contient le nom de serveur ou null si aucune valeur n’est définie.  
  
## <a name="remarks"></a>Notes  
 Le nom du serveur est le nom d’hôte de l’ordinateur cible qui est en cours d’exécution [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)]. Si la propriété getServerName n’est pas définie, getServerName retourne la valeur par défaut null.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

