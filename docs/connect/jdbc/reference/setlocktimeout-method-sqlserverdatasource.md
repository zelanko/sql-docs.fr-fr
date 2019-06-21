---
title: Méthode setLockTimeout (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setLockTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 10dca5aa-1851-4326-9ae9-7a8430d12d11
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 32f61572dca7124e552a9d40497a3385bc243b31
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66790465"
---
# <a name="setlocktimeout-method-sqlserverdatasource"></a>Méthode setLockTimeout (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit une valeur **int** qui indique le nombre de millisecondes pendant lesquelles la base de données patiente avant de signaler un dépassement de délai d’attente de verrou.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setLockTimeout(int lockTimeout)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *lockTimeout*  
  
 Valeur **int** contenant le nombre de millisecondes à attendre.  
  
## <a name="remarks"></a>Notes  
 Le délai d'un verrou correspond au nombre de millisecondes à attendre avant que la base de données ne rapporte l'expiration d'un délai de verrou. La valeur par défaut de -1 indique une durée d'attente indéfinie. Si elle est spécifiée, cette valeur sera la valeur par défaut pour toutes les instructions de la connexion.  
  
> [!NOTE]  
>  La valeur 0 indique qu'il n'y aura pas d'attente. Si la propriété lockTimeout n’est pas définie, la méthode [getLockTimeout](../../../connect/jdbc/reference/getlocktimeout-method-sqlserverdatasource.md) retourne la valeur par défaut (-1).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
