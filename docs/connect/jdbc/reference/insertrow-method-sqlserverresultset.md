---
title: insertRow, méthode (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.insertRow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 363d1008-1396-4fc0-8e27-c9ba2499e7f1
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: cf6b427cfaaf736fb7ea3862554bde172f2a0247
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66801229"
---
# <a name="insertrow-method-sqlserverresultset"></a>insertRow, méthode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Ajoute le contenu de la ligne d’insertion à cet objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) et à la base de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void insertRow()  
```  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode insertRow est spécifiée par la méthode insertRow dans l’interface java.sql.ResultSet.  
  
 Le curseur doit se trouver sur la ligne d'insertion lorsque cette méthode est appelée. Après l'appel de cette méthode, le curseur reste sur la ligne d'insertion et le jeu de résultats demeure en mode insertion.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
