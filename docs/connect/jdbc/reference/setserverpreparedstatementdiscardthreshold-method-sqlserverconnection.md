---
title: Méthode Setserverpreparedstatementdiscardthreshold, (SQLServerConnection) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.setServerPreparedStatementDiscardThreshold
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8f66746b15e96f49d96b428e8cf8844eeea12a12
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67972921"
---
# <a name="setserverpreparedstatementdiscardthreshold-method-sqlserverconnection"></a>setServerPreparedStatementDiscardThreshold, méthode (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Spécifie le comportement d’une instance de connexion spécifique. Ce paramètre contrôle le nombre d’actions d’instruction préparée en suspens (sp_unprepare) qui peuvent être en attente par connexion avant qu’un appel pour nettoyer les descripteurs en suspens sur le serveur soit exécuté. Lorsque le paramètre est < = 1 les actions d’annulation de la préparation sont exécutées immédiatement lors de la fermeture de l’instruction préparée. Si la valeur est définie sur > 1, ces appels sont regroupés pour éviter la surcharge de l’appel de sp_unprepare trop souvent.


## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setServerPreparedStatementDiscardThreshold(boolean thresholdValue)  
```  

#### <a name="parameters"></a>Paramètres  
 *thresholdValue*  
 
 Nouvelle valeur de la propriété de connexion **serverPreparedStatementDiscardThreshold** .  
 
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Notes  
 Cette méthode est disponible dans la version 6,4 et les versions ultérieures du pilote JDBC.
 
## <a name="see-also"></a>Voir aussi  
 [SQLServerConnection, membres](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
