---
title: Méthode setLastUpdateCount (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setLastUpdateCount
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5487631a-1107-4169-84ca-b77fd09bea66
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3369fbc84cb16ed0f9b587ed20fe7fe368d11b02
ms.sourcegitcommit: 0d6e4cafbb5d746e7d00fdacf8f3ce16f3023306
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49084909"
---
# <a name="setlastupdatecount-method-sqlserverdatasource"></a>Méthode setLastUpdateCount (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit une valeur **booléenne** qui indique si la propriété lastUpdateCount est activée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setLastUpdateCount(boolean lastUpdateCount)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *lastUpdateCount*  
  
 **true** si lastUpdateCount est activée. Dans le cas contraire, la valeur est **false**.  
  
## <a name="remarks"></a>Notes   
 Si la propriété lastUpdateCount a la valeur **true**, [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] retourne uniquement le dernier nombre de mises à jour à partir d’une instruction SQL transmise au serveur. Si la propriété lastUpdateCount a la valeur **false**, le pilote retourne tous les nombres de mise à jour, y compris ceux retournés par les déclencheurs qui ont pu s’activer. Si la propriété lastUpdateCount n’est pas définie, la méthode [getLastUpdateCount](../../../connect/jdbc/reference/getlastupdatecount-method-sqlserverdatasource.md) retourne la valeur par défaut (**true**).  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
