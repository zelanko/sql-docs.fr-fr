---
title: Next, méthode (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.next
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 60248447-6908-4036-a779-a501453cd553
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c2b5611c9f925c95a49982f8f9c936a6d84952f4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47702839"
---
# <a name="next-method-sqlserverresultset"></a>next, méthode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Déplace le curseur d'une ligne vers le bas depuis sa position actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean next()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si la nouvelle ligne actuelle est valide. **false** s’il n’existe plus aucune ligne à traiter.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode next est spécifiée par la méthode next de l’interface java.sql.ResultSet.  
  
 Un curseur du jeu de résultats est positionné initialement avant la première ligne. Le premier appel de la méthode next fait de la première ligne la ligne actuelle, le deuxième appel fait de la deuxième ligne la ligne actuelle, et ainsi de suite.  
  
 Si un flux d’entrée est ouvert pour la ligne actuelle, l’appel de la méthode next le ferme implicitement. Une chaîne d’avertissement pour l’objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) est effacée à la lecture d’une nouvelle ligne.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
