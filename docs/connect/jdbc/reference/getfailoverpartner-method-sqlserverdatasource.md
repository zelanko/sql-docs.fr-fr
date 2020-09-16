---
description: Méthode getFailoverPartner (SQLServerDataSource)
title: Méthode getFailoverPartner (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getFailoverPartner
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 885f927f-9c48-42e0-a7fb-fd936d2b8130
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 607f14bab8795ba3dfebd33e2c179f85897f210a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88436061"
---
# <a name="getfailoverpartner-method-sqlserverdatasource"></a>Méthode getFailoverPartner (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne le nom du serveur de basculement utilisé dans une configuration de mise en miroir de bases de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public string getFailoverPartner()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **Chaîne** contenant le nom du partenaire de basculement, ou Null si aucun n’est défini.  
  
## <a name="remarks"></a>Notes  
 La valeur retournée par cette méthode reflète le nom du partenaire de basculement défini avec la méthode [setFailoverPartner](../../../connect/jdbc/reference/setfailoverpartner-method-sqlserverdatasource.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
