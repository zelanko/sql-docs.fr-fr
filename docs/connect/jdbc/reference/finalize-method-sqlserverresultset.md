---
title: Finalize, méthode (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.finalize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 49bc879d-822b-42da-bc20-2394865f1f0f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3e1b8a5435d6923015c2d3c29eef5031f3d5b2f4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47622787"
---
# <a name="finalize-method-sqlserverresultset"></a>finalize, méthode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ferme explicitement cet objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void finalize()  
```  
  
## <a name="remarks"></a>Notes   
 Ferme le jeu de résultats si l'application omet de le faire. Cette méthode existe uniquement pour la conformité avec la spécification JDBC. Comme la machine virtuelle Java (JVM) ne garantit pas lorsqu'un finaliseur aura la chance de s'exécuter, les applications qui négligent de fermer explicitement leurs jeux de résultats pourront toujours effectuer un interblocage sur une autre instruction utilisant la même connexion et bloquée sur une ressource de serveur commune, telle que des verrous de ligne.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
