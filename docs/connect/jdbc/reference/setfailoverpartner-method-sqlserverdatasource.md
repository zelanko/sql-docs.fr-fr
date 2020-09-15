---
description: Méthode setFailoverPartner (SQLServerDataSource)
title: Méthode setFailoverPartner (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setFailoverPartner
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5310b7c2-9d10-474f-ad3a-218fe5da694b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c90a6cd4850ad746bafde4646cd459fbcff3e825
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88431881"
---
# <a name="setfailoverpartner-method-sqlserverdatasource"></a>Méthode setFailoverPartner (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le nom du serveur de basculement utilisé dans une configuration de mise en miroir de bases de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setFailoverPartner(java.lang.String serverName)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *serverName*  
  
 **Chaîne** contenant le nom du serveur de basculement.  
  
## <a name="remarks"></a>Notes  
 La valeur définie par cette méthode est utilisée en cas d'échec de connexion initiale avec le serveur principal ; une fois la connexion initiale établie, cette valeur est ignorée. La méthode [setDatabaseName](../../../connect/jdbc/reference/setdatabasename-method-sqlserverdatasource.md) doit également être utilisée conjointement avec cette méthode ; sinon, une exception est levée.  
  
 Le pilote ne prend pas en charge la spécification du numéro de port du serveur de basculement lorsque le nom de ce serveur est défini. Cependant, l’appel des méthodes [setServerName](../../../connect/jdbc/reference/setservername-method-sqlserverdatasource.md) et [setInstanceName](../../../connect/jdbc/reference/setinstancename-method-sqlserverdatasource.md) avec la méthode [setFailoverPartner](../../../connect/jdbc/reference/setfailoverpartner-method-sqlserverdatasource.md) est pris en charge.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
