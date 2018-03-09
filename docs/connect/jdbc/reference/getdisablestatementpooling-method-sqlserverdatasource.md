---
title: "getDisableStatementPooling (méthode) (SQLServerDataSource) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2018
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
ms.assetid: 
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 33c4de8e0ecd135dad43968e4f2cd547928b4176
ms.sourcegitcommit: 9d0467265e052b925547aafaca51e5a5e93b7e38
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2018
---
# <a name="getdisablestatementpooling-method-sqlserverdatasource"></a>getDisableStatementPooling (méthode) (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne la valeur de **disableStatementPooling** propriété de connexion. Ce paramètre contrôle si le regroupement d’instructions est activé ou non pour cette connexion.

  
## <a name="syntax"></a>Syntaxe  
  
```
public boolean getDisableStatementPooling();  
```  
  
## <a name="return-value"></a>Valeur retournée  
 A **booléenne** qui contient la valeur de **disableStatementPooling** propriété de connexion.
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Notes  
 Cette méthode est disponible à partir de la version du pilote JDBC 6.4 et ultérieur.
 
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource Members](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
