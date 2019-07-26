---
title: Méthode insertRow (SQLServerResultSet) | Microsoft Docs
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
ms.openlocfilehash: 0f2e6148572d6ec6c7e9b52a704d79e8a9124ccf
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67977882"
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
 Cette méthode insertRow est spécifiée par la méthode insertRow dans l’interface java. Sql. ResultSet.  
  
 Le curseur doit se trouver sur la ligne d'insertion lorsque cette méthode est appelée. Après l'appel de cette méthode, le curseur reste sur la ligne d'insertion et le jeu de résultats demeure en mode insertion.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
