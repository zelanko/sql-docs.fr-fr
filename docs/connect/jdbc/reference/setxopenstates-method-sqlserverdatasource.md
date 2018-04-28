---
title: Méthode setXopenStates (SQLServerDataSource) | Documents Microsoft
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
- SQLServerDataSource.setXopenStates
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9723591f-e987-426f-b70a-07f5c70dc094
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 201c0b34da3198ed0f6067944d581fb9bc696bd4
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="setxopenstates-method-sqlserverdatasource"></a>Méthode setXopenStates (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit un **booléenne** valeur qui indique si la conversion d’états SQL en États compatibles XOPEN est activée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setXopenStates(boolean xopenStates)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *xopenStates*  
  
 **true** si la conversion d’états SQL en États compatibles XOPEN est activée. Dans le cas contraire, la valeur est **false**.  
  
## <a name="remarks"></a>Notes  
 Si la propriété xopenStates a la valeur **true**, le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] convertira les États SQL en États compatibles XOPEN. La valeur par défaut est **false**, ce qui entraîne le pilote JDBC générer des codes d’état SQL 99. Si xopenStates n’est pas définie, la [getXopenStates](../../../connect/jdbc/reference/getxopenstates-method-sqlserverdatasource.md) méthode retourne la valeur par défaut **false**.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
