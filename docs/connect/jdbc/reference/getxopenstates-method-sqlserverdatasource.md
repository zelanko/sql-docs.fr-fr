---
title: Méthode getXopenStates (SQLServerDataSource) | Documents Microsoft
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
- SQLServerDataSource.getXopenStates
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: de6fdf6b-8345-4490-b35e-7115b61e782e
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5657adea99d7a7ba3e6a5d51ebf39f84cd39de08
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="getxopenstates-method-sqlserverdatasource"></a>Méthode getXopenStates (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne une valeur **booléenne** qui indique si la conversion d'états SQL en états compatibles XOPEN est activée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean getXopenStates()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si la conversion d’états SQL en États compatibles XOPEN est activée. Dans le cas contraire, la valeur est **false**.  
  
## <a name="remarks"></a>Notes  
 Si la propriété xopenStates a la valeur **true**, le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] convertit les états SQL en états compatibles XOPEN. La valeur par défaut est **false**, qui entraîne le pilote JDBC à générer des codes d'état SQL 99. Si xopenStates n’a aucune valeur, la méthode getXopenStates retourne la valeur par défaut **false**.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
