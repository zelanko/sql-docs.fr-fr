---
title: Méthode getServerPreparedStatementDiscardThreshold (SQLServerConnection) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.getServerPreparedStatementDiscardThreshold
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 87d7f85799524e3ac7c0e4d99608ce1d82b8f2fc
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67979929"
---
# <a name="getserverpreparedstatementdiscardthreshold-method-sqlserverconnection"></a>getServerPreparedStatementDiscardThreshold, méthode (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Retourne la valeur de la propriété de connexion **serverPreparedStatementDiscardThreshold**. Ce paramètre contrôle le nombre d’actions d’instruction préparée en attente (sp_unprepare) qui peuvent être en attente par connexion avant l’exécution d’un appel pour nettoyer les handles en attente sur le serveur. Si le paramètre est < = 1, les actions d’annulation de la préparation sont exécutées immédiatement à la fermeture de l’instruction préparée. S’il est défini sur > 1, ces appels sont regroupés pour éviter une surcharge trop fréquente liée aux appels à sp_unprepare. La valeur par défaut de cette option peut être modifiée en appelant getDefaultServerPreparedStatementDiscardThreshold().

## <a name="syntax"></a>Syntaxe  
  
```  
  
public int getServerPreparedStatementDiscardThreshold()  
```  

## <a name="return-value"></a>Valeur de retour
 **int** qui contient la valeur de la propriété de connexion **serverPreparedStatementDiscardThreshold**.

## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Notes  
 Cette méthode est disponible dans la version 6.4 et versions ultérieures du pilote JDBC.
 
## <a name="see-also"></a>Voir aussi  
 [SQLServerConnection, membres](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
