---
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 39195742d8b6a2a03b0b2c835f47d0ba42735791
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47730457"
---
# <a name="getfailoverpartner-method-sqlserverdatasource"></a>Méthode getFailoverPartner (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne le nom du serveur de basculement utilisé dans une configuration de mise en miroir de bases de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public string getFailoverPartner()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Un **chaîne** qui contient le nom du partenaire de basculement, ou null si aucun n’est défini.  
  
## <a name="remarks"></a>Notes   
 La valeur retournée par cette méthode reflète le nom du partenaire de basculement défini avec la méthode [setFailoverPartner](../../../connect/jdbc/reference/setfailoverpartner-method-sqlserverdatasource.md).  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
