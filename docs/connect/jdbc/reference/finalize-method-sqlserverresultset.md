---
title: Méthode finalize (SQLServerResultSet) | Microsoft Docs
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
ms.openlocfilehash: 7afb8728b92ac7460173950bf42e38f968e056af
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67954566"
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
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
