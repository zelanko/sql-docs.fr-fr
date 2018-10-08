---
title: getserverpreparedstatementdiscardthreshold, méthode (SQLServerDataSource) | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 09762036b607f5d124ae50a333c99eff67649079
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47633807"
---
# <a name="getserverpreparedstatementdiscardthreshold-method-sqlserverdatasource"></a>getServerPreparedStatementDiscardThreshold, méthode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne la valeur de **serverPreparedStatementDiscardThreshold** propriété de connexion. Ce paramètre contrôle préparé en suspens combien rejet instruction actions (sp_unprepare) peuvent être en attente par connexion avant l’exécution d’un appel pour nettoyer les handles en attente sur le serveur. Lorsque le paramètre est < = 1 ces actions sont exécutées immédiatement sur une instruction préparée fermer. Si cette valeur est définie sur 1 > ces appels sont regroupés afin d’éviter le traitement de l’appel de sp_unprepare trop souvent.

  
## <a name="syntax"></a>Syntaxe  
  
```
public int getServerPreparedStatementDiscardThreshold();  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Retourne le **int** valeur de la **serverPreparedStatementDiscardThreshold** propriété de connexion.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Notes   
 Cette méthode est disponible à partir de la version du pilote JDBC 6.4 et ultérieur.
 
## <a name="see-also"></a> Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
