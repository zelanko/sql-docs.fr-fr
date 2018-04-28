---
title: Finalize (méthode) (SQLServerResultSet) | Documents Microsoft
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
- SQLServerResultSet.finalize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 49bc879d-822b-42da-bc20-2394865f1f0f
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d8f3778d4cc069e95b26bd2f7648e590c4cf33f3
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="finalize-method-sqlserverresultset"></a>Finalize (méthode) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Cela ferme explicitement [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objet.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void finalize()  
```  
  
## <a name="remarks"></a>Notes  
 Ferme le jeu de résultats si l'application omet de le faire. Cette méthode existe uniquement pour la conformité avec la spécification JDBC. Comme la machine virtuelle Java (JVM) ne garantit pas lorsqu'un finaliseur aura la chance de s'exécuter, les applications qui négligent de fermer explicitement leurs jeux de résultats pourront toujours effectuer un interblocage sur une autre instruction utilisant la même connexion et bloquée sur une ressource de serveur commune, telle que des verrous de ligne.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
