---
title: GetType, méthode (SQLServerResultSet) | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 38cc11c791666ebefadf71a412ea5a5858c03f34
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66786153"
---
# <a name="gettype-method-sqlserverresultset"></a>getType, méthode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère le type de curseur de cet objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int getType()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Un **int** qui indique le type de curseur en cours, ce qui peut prendre l’une des valeurs suivantes :  
  
 ResultSet.TYPE_FORWARD_ONLY  
  
 ResultSet.TYPE_SCROLL_INSENSITIVE  
  
 ResultSet.TYPE_SCROLL_SENSITIVE  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getTime est spécifiée par la méthode getTime de l’interface java.sql.ResultSet.  
  
 Cette méthode peut être utilisée pour déterminer le type du curseur réel. Si l'application a sélectionné TYPE_FORWARD_ONLY ou utilisé un type de curseur par défaut, TYPE_FORWARD_ONLY sera retourné.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
