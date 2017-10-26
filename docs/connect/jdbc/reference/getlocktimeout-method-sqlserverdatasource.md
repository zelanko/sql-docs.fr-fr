---
title: "Méthode getLockTimeout (SQLServerDataSource) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDataSource.getLockTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 676094e9-ec18-4524-9b21-1f9c5b16dd52
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: edbd984352f2b75711e9fc9a445a84066fb9f0ac
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

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
 [Membres de SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  

