---
title: "Méthode setFailoverPartner (SQLServerDataSource) | Documents Microsoft"
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
apiname: SQLServerDataSource.setFailoverPartner
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 5310b7c2-9d10-474f-ad3a-218fe5da694b
caps.latest.revision: "17"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7aa59563e6980ef29f3e53e19519b83bcac8d721
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="setfailoverpartner-method-sqlserverdatasource"></a>Méthode setFailoverPartner (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le nom du serveur de basculement qui est utilisé dans une configuration de mise en miroir de base de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setFailoverPartner(java.lang.String serverName)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *nom du serveur*  
  
 A **chaîne** qui contient le nom du serveur de basculement.  
  
## <a name="remarks"></a>Notes  
 La valeur définie par cette méthode est utilisée en cas d'échec de connexion initiale avec le serveur principal ; une fois la connexion initiale établie, cette valeur est ignorée. Le [setDatabaseName](../../../connect/jdbc/reference/setdatabasename-method-sqlserverdatasource.md) méthode doit également être utilisée conjointement avec cette méthode ou une exception sera levée.  
  
 Le pilote ne prend pas en charge la spécification du numéro de port du serveur de basculement lorsque le nom de ce serveur est défini. Toutefois, l’appel du [setServerName](../../../connect/jdbc/reference/setservername-method-sqlserverdatasource.md) (méthode) et le [setInstanceName](../../../connect/jdbc/reference/setinstancename-method-sqlserverdatasource.md) méthode avec la [setFailoverPartner](../../../connect/jdbc/reference/setfailoverpartner-method-sqlserverdatasource.md) méthode est prise en charge.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
