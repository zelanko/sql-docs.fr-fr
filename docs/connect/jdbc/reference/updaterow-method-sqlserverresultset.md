---
title: Méthode updateRow (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- MSQLServerResultSet.updateRow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: cfced0ca-a281-40dc-8d2f-370d5f0bf12b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0e33da1c8873bdc2d69c93d533860d9b9f5e227d
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67998352"
---
# <a name="updaterow-method-sqlserverresultset"></a>updateRow, méthode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Met à jour la base de données sous-jacente avec le nouveau contenu de la ligne actuelle de cet objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void updateRow()  
```  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode updateRow est spécifiée par la méthode updateRow de l’interface java.sql.ResultSet.  
  
 Cette méthode ne peut pas être appelée lorsque le curseur se trouve sur la ligne d'insertion.  
  
 Si cette méthode est appelée alors qu'aucune valeur de colonne n'a changé, une exception est levée.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
