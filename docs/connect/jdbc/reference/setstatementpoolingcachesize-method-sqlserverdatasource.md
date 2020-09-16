---
description: setStatementPoolingCacheSize, méthode (SQLServerDataSource)
title: Méthode setStatementPoolingCacheSize (SQLServerDataSource) | Microsoft Docs
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
ms.openlocfilehash: 07f2ab026fa0432124b554d31e52cf179ddaceea
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88450781"
---
# <a name="setstatementpoolingcachesize-method-sqlserverdatasource"></a>setStatementPoolingCacheSize, méthode (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit la taille du cache d’instructions préparées pour cette connexion. Fonctionne si disableStatementPooling est définie sur false et que la valeur est > 0.
  
## <a name="syntax"></a>Syntaxe  
  
```

public void setStatementPoolingCacheSize(boolean statementPoolingCacheSize);  
```  
  
#### <a name="parameters"></a>Paramètres  
 *statementPoolingCacheSize*  
  
 Nouvelle valeur de la propriété de connexion **statementPoolingCacheSize**.  

## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Notes  
 Cette méthode est disponible dans la version 6.4 et versions ultérieures du pilote JDBC.
 
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
