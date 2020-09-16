---
description: finalize, méthode (SQLServerResultSet)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f6f232e7755dd975edaa7b255e5ffe6dd9f85091
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88437591"
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
  
  
