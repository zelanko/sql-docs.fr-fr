---
title: setXopenStates, méthode (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setXopenStates
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9723591f-e987-426f-b70a-07f5c70dc094
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 42c8e22ed8fe17ea72accee7c1a58b49abf97134
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80901465"
---
# <a name="setxopenstates-method-sqlserverdatasource"></a>Méthode setXopenStates (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Définit une valeur **booléenne** qui indique si la conversion d’états SQL en états compatibles XOPEN est activée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setXopenStates(boolean xopenStates)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *xopenStates*  
  
 **true** si la conversion d’états SQL en états compatibles XOPEN est activée. Dans le cas contraire, la valeur est **false**.  
  
## <a name="remarks"></a>Notes  
 Si la propriété xopenStates a la valeur **true**, le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] convertit les états SQL en états compatibles XOPEN. La valeur par défaut est **false**, qui entraîne le pilote JDBC à générer des codes d'état SQL 99. Si xopenStates n’est pas défini, la méthode [getXopenStates](../../../connect/jdbc/reference/getxopenstates-method-sqlserverdatasource.md) retourne la valeur par défaut (**false**).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
