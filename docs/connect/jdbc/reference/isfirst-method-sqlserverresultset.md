---
title: Méthode isFirst (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.isFirst
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2ff94b95-32ad-4378-8bb1-970030527bb2
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b847361621ad8d44840aa4bab02e4877128e8f48
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67977625"
---
# <a name="isfirst-method-sqlserverresultset"></a>isFirst, méthode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère l’information indiquant si le curseur se trouve sur la première ligne de cet objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean isFirst()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si le curseur se trouve sur la première ligne. **false** si le curseur se trouve à une autre position ou si le jeu de résultats ne contient aucune ligne.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode isFirst est spécifiée par la méthode isFirst de l’interface java.sql.ResultSet.  
  
 Si cette méthode est utilisée avec les curseurs avant et dynamiques, une exception est levée.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
