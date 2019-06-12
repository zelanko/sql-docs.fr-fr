---
title: setStatementPoolingCacheSize Method (SQLServerConnection) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.setStatementPoolingCacheSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ''
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: dd113dec0a7ed8ba8bdcf66bca5cfbd454d5a500
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66762303"
---
# <a name="setstatementpoolingcachesize-method-sqlserverconnection"></a>setStatementPoolingCacheSize, méthode (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

 Définit la taille du cache d’instruction préparée pour cette connexion. Fonctionne si disableStatementPooling est définie sur false et la valeur > 0.

## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setStatementPoolingCacheSize(int statementPoolingCacheSize)  
```  

#### <a name="parameters"></a>Paramètres  
 *statementPoolingCacheSize*  
  
 La nouvelle valeur de la **regroupement d’instructions** propriété de connexion.  

## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Notes  
 Cette méthode est disponible à partir de la version du pilote JDBC 6.4 et ultérieur.
 
## <a name="see-also"></a>Voir aussi  
 [SQLServerConnection, membres](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection, classe](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
