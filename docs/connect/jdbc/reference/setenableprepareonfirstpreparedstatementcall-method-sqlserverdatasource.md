---
title: setenableprepareonfirstpreparedstatementcall, méthode (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 18cd626fb3eee4690d87dd40edd50e64a4dcd98e
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66779135"
---
# <a name="setenableprepareonfirstpreparedstatementcall-method-sqlserverdatasource"></a>setEnablePrepareOnFirstPreparedStatementCall, méthode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Spécifie le comportement pour une instance de connexion spécifique. Si cette configuration est false, la première exécution d’une instruction préparée appelle sp_executesql et n’a pas préparer une instruction, une fois que la deuxième exécution se produit, il appelle sp_prepexec et en fait le programme d’installation un descripteur d’instruction préparée. Suivant les exécutions appellera sp_execute. Cela évite la nécessité de sp_unprepare sur instruction préparée fermer si l’instruction est exécutée uniquement une fois.  
## <a name="syntax"></a>Syntaxe  
  
```
public void setEnablePrepareOnFirstPreparedStatementCall(boolean enablePrepareOnFirstPreparedStatementCall);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *enablePrepareOnFirstPreparedStatementCall*  
  
 La nouvelle valeur de la **enablePrepareOnFirstPreparedStatementCall** propriété de connexion.  

## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Notes  
 Cette méthode est disponible à partir de la version du pilote JDBC 6.4 et ultérieur.
 
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
