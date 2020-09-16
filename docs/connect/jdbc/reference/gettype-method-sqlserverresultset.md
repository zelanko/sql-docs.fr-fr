---
description: getType, méthode (SQLServerResultSet)
title: Méthode getType (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getType
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ffbc4a02-e851-431c-bc1a-7ab381d982bb
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0c01dc19b6f9dfd1f1816c209f7c2168a68ceb85
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88433961"
---
# <a name="gettype-method-sqlserverresultset"></a>getType, méthode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère le type de curseur de cet objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int getType()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **int** indiquant le type de curseur actuel, qui peut être l'une des valeurs suivantes :  
  
 ResultSet.TYPE_FORWARD_ONLY  
  
 ResultSet.TYPE_SCROLL_INSENSITIVE  
  
 ResultSet.TYPE_SCROLL_SENSITIVE  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getType est spécifiée par la méthode getType de l’interface java.sql.ResultSet.  
  
 Cette méthode peut être utilisée pour déterminer le type du curseur réel. Si l'application a sélectionné TYPE_FORWARD_ONLY ou utilisé un type de curseur par défaut, TYPE_FORWARD_ONLY sera retourné.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
