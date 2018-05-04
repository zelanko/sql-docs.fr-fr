---
title: Méthode getLockTimeout (SQLServerDataSource) | Documents Microsoft
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
- SQLServerDataSource.getLockTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 676094e9-ec18-4524-9b21-1f9c5b16dd52
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f01072360ecb2a917527b589d9762e5764fef0e4
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="getlocktimeout-method-sqlserverdatasource"></a>Méthode getLockTimeout (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne un **int** valeur qui indique le nombre de millisecondes pendant lesquelles la base de données attend avant de signaler un délai de verrouillage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int getLockTimeout()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Un **int** valeur qui contient le nombre de millisecondes d’attente de la base de données.  
  
## <a name="remarks"></a>Notes  
 Le délai d'un verrou correspond au nombre de millisecondes à attendre avant que la base de données ne rapporte l'expiration d'un délai de verrou. La valeur par défaut de -1 indique une durée d'attente indéfinie. Si elle est spécifiée, cette valeur sera la valeur par défaut pour toutes les instructions de la connexion.  
  
> [!NOTE]  
>  La valeur 0 indique qu'il n'y aura pas d'attente. Si la propriété lockTimeout n'est pas définie, la méthode getLockTimeout retourne la valeur par défaut de -1.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
