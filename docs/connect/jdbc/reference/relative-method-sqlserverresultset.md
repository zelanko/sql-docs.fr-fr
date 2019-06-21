---
title: relative, méthode (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.relative
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2bcdbb69-95fd-4ae8-8488-1a75a91fe2e0
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: b8907a5e2eb2ead5202e8aec9fd5320a6047a5f4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66797709"
---
# <a name="relative-method-sqlserverresultset"></a>relative, méthode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Déplace le curseur en fonction du nombre de lignes spécifié, par rapport à la ligne actuelle, dans une direction positive ou négative.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean relative(int nRows)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *nRows*  
  
 Un **int** qui indique le nombre de lignes à déplacer.  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si le curseur se trouve sur une ligne. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode relative est spécifiée par la méthode relative dans l’interface java.sql.ResultSet.  
  
 Toute tentative de déplacement au-delà de la première ou de la dernière ligne dans le jeu de résultats positionne le curseur avant ou après la première ou la dernière ligne. Appeler `relative(0)` est valide, mais ne modifie pas la position du curseur.  
  
 Appeler la méthode `relative(1)` a le même effet qu’appeler la méthode [next](../../../connect/jdbc/reference/next-method-sqlserverresultset.md). Appeler la méthode `relative(-1)` a le même effet qu’appeler la méthode [previous](../../../connect/jdbc/reference/previous-method-sqlserverresultset.md).  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
