---
title: Méthode getLastUpdateCount (SQLServerDataSource) | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
apiname:
- SQLServerDataSource.getLastUpdateCount
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4c4fbb24-0b02-42da-928c-a903bb591cc7
caps.latest.revision: 17
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 5a22f963d409657b645ad04b50c260fc1576b980
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="getlastupdatecount-method-sqlserverdatasource"></a>Méthode getLastUpdateCount (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne un **booléenne** valeur qui indique si la propriété lastUpdateCount est activée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean getLastUpdateCount()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si lastUpdateCount est activée. Dans le cas contraire, la valeur est **false**.  
  
## <a name="remarks"></a>Notes  
 Si la propriété lastUpdateCount a la valeur **true**, le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] retourne uniquement le dernier nombre de mises à jour à partir d’une instruction SQL transmise au serveur. Si la propriété lastUpdateCount a la valeur **false**, le pilote retourne toutes les mises à jour multiples, y compris ceux retournés par des déclencheurs qui ont peuvent se déclencher. Si la propriété lastUpdateCount n’est pas définie, la méthode getLastUpdateCount retourne la valeur par défaut **true**.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
