---
title: Méthode getLoginTimeout (SQLServerDataSource) | Documents Microsoft
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
ms.topic: conceptual
apiname:
- SQLServerDataSource.getLoginTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 316f067c-9e08-456a-af19-b80b0bbd4a5c
caps.latest.revision: 13
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: dcaccc8a16561f43b4ada72d1e07bad291b6ec2c
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="getlogintimeout-method-sqlserverdatasource"></a>Méthode getLoginTimeout (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne le nombre de secondes que ce [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) objet doit patienter lors de la tentative établir une connexion.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int getLoginTimeout()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Un **int** valeur qui représente le nombre de secondes d’attente.  
  
## <a name="remarks"></a>Notes  
 Si l'application ne spécifie pas explicitement une valeur de délai d'attente, cette méthode retourne une valeur par défaut de 15 secondes.  
  
 Cette méthode getLoginTimeout est spécifiée par la méthode getLoginTimeout dans l’interface javax.sql.DataSource.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
