---
description: getServerPreparedStatementDiscardThreshold, méthode (SQLServerDataSource)
title: Méthode getServerPreparedStatementDiscardThreshold (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e779955f77be3891bb3f7479b4a40fb30b3d56ac
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88434541"
---
# <a name="getserverpreparedstatementdiscardthreshold-method-sqlserverdatasource"></a>getServerPreparedStatementDiscardThreshold, méthode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne la valeur de la propriété de connexion **serverPreparedStatementDiscardThreshold**. Ce paramètre contrôle le nombre d’actions d’instruction préparée en attente (sp_unprepare) qui peuvent être en attente par connexion avant l’exécution d’un appel pour nettoyer les handles en attente sur le serveur. Lorsque le paramètre est < = 1, les actions d’annulation de la préparation sont exécutées immédiatement à la fermeture de l’instruction préparée. Si cette valeur est définie sur > 1, ces appels sont regroupés pour éviter une surcharge trop fréquente liée aux appels à sp_unprepare.

  
## <a name="syntax"></a>Syntaxe  
  
```
public int getServerPreparedStatementDiscardThreshold();  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne la valeur **int** de la propriété de connexion **serverPreparedStatementDiscardThreshold**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Notes  
 Cette méthode est disponible dans la version 6.4 et versions ultérieures du pilote JDBC.
 
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
