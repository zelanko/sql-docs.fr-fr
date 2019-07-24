---
title: Méthode Getserverpreparedstatementdiscardthreshold, (SQLServerDataSource) | Microsoft Docs
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
ms.openlocfilehash: 3f91b75b5c70029d53582b8b6ed4655485fd3fcf
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67979906"
---
# <a name="getserverpreparedstatementdiscardthreshold-method-sqlserverdatasource"></a>getServerPreparedStatementDiscardThreshold, méthode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne la valeur de la propriété de connexion **serverPreparedStatementDiscardThreshold** . Ce paramètre contrôle le nombre d’actions d’instruction préparée en suspens (sp_unprepare) qui peuvent être en attente par connexion avant qu’un appel pour nettoyer les descripteurs en suspens sur le serveur soit exécuté. Lorsque le paramètre est < = 1 les actions d’annulation de préparation sont exécutées immédiatement lors de la fermeture de l’instruction préparée. Si cette valeur est définie sur > 1, ces appels sont regroupés pour éviter la surcharge d’appel de sp_unprepare trop souvent.

  
## <a name="syntax"></a>Syntaxe  
  
```
public int getServerPreparedStatementDiscardThreshold();  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Retourne la valeur **int** de la propriété de connexion **serverPreparedStatementDiscardThreshold** .  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Notes  
 Cette méthode est disponible dans la version 6,4 et les versions ultérieures du pilote JDBC.
 
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
