---
description: Méthode getXopenStates (SQLServerDataSource)
title: getXopenStates, méthode (SQLServerDataSource) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getXopenStates
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: de6fdf6b-8345-4490-b35e-7115b61e782e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 654b7a56a98b0a70599e21ef55a12d4db420890d
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88433711"
---
# <a name="getxopenstates-method-sqlserverdatasource"></a>Méthode getXopenStates (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne une valeur **booléenne** qui indique si la conversion d'états SQL en états compatibles XOPEN est activée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean getXopenStates()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **true** si la conversion d'états SQL en états compatibles XOPEN est activée. Dans le cas contraire, la valeur est **false**.  
  
## <a name="remarks"></a>Notes  
 Si la propriété xopenStates a la valeur **true**, le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] convertit les états SQL en états compatibles XOPEN. La valeur par défaut est **false**, qui entraîne le pilote JDBC à générer des codes d'état SQL 99. Si xopenStates n’est pas défini, la méthode getXopenStates retourne la valeur par défaut (**false**).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDataSource, membres](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource, classe](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
