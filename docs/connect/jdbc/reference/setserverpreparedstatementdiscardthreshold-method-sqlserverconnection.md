---
title: "setServerPreparedStatementDiscardThreshold (méthode) (SQLServerConnection) | Documents Microsoft"
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
apiname:
- SQLServerConnection.setServerPreparedStatementDiscardThreshold
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 427258eb9d216f867e244ebb1b80af9036a09a66
ms.sourcegitcommit: 9d0467265e052b925547aafaca51e5a5e93b7e38
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2018
---
# <a name="setserverpreparedstatementdiscardthreshold-method-sqlserverconnection"></a>setServerPreparedStatementDiscardThreshold (méthode) (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Spécifie le comportement d’une instance de connexion spécifique. Ce paramètre contrôle préparé en suspens combien rejet instruction actions (sp_unprepare) peuvent être en attente par connexion avant l’exécution d’un appel à nettoyer les handles en attente sur le serveur. Lorsque le paramètre est < = 1 Annuler-préparer les actions sont exécutées immédiatement sur une instruction préparée fermer. Si la valeur est définie sur 1 > ces appels sont regroupées afin d’éviter le traitement de l’appel sp_unprepare trop souvent.


## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setServerPreparedStatementDiscardThreshold(boolean thresholdValue)  
```  

#### <a name="parameters"></a>Paramètres  
 *thresholdValue*  
 
 La nouvelle valeur de la **serverPreparedStatementDiscardThreshold** propriété de connexion.  
 
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Notes  
 Cette méthode est disponible à partir de la version du pilote JDBC 6.4 et ultérieur.
 
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
