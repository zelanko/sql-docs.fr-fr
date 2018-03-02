---
title: "getEnablePrepareOnFirstPreparedStatementCall (méthode) (SQLServerDataSource) | Documents Microsoft"
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
ms.openlocfilehash: 766a00c0a92c3df65e39bbfcd7ad87c5529a5b98
ms.sourcegitcommit: 9d0467265e052b925547aafaca51e5a5e93b7e38
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2018
---
# <a name="getenableprepareonfirstpreparedstatementcall-method-sqlserverdatasource"></a>getEnablePrepareOnFirstPreparedStatementCall (méthode) (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne la valeur de **enablePrepareOnFirstPreparedStatementCall** propriété de connexion. Si cette configuration renvoie false la première exécution d’une instruction préparée sera appeler sp_executesql et n’a pas préparer une instruction, une fois que la deuxième exécution se produit, elle appelle sp_prepexec et réellement le programme d’installation un descripteur d’instruction préparée. Suivant les exécutions appelle sp_execute. Cela évite la nécessité de sp_unprepare sur instruction préparée fermer si l’instruction est exécutée uniquement si une seule fois. 
  
## <a name="syntax"></a>Syntaxe  
  
```
public boolean getEnablePrepareOnFirstPreparedStatementCall();  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Retourne le **booléenne** valeur de la **enablePrepareOnFirstPreparedStatementCall** propriété de connexion.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Notes  
 Cette méthode est disponible à partir de la version du pilote JDBC 6.4 et ultérieur.
 
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource Members](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
