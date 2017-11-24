---
title: "Méthode setLoginTimeout (SQLServerDataSource) | Documents Microsoft"
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
apiname: SQLServerDataSource.setLoginTimeout
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: b63d1cf4-dc1b-4e35-9a56-50436642eaaf
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4a65f835792fc342cbbcc3803c9a3be6d0bb9214
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="setlogintimeout-method-sqlserverdatasource"></a>Méthode setLoginTimeout (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit le nombre de secondes que cela [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md) objet doit patienter lors de la tentative établir une connexion.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setLoginTimeout(int loginTimeout)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *loginTimeout*  
  
 Un **int** valeur qui représente le nombre de secondes d’attente. Zéro indique que le délai d'attente correspond au délai d'attente système par défaut, lequel est de 15 secondes.  
  
## <a name="remarks"></a>Notes  
 Cette méthode setLoginTimeout est spécifiée par la méthode setLoginTimeout dans l’interface javax.sql.DataSource.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
