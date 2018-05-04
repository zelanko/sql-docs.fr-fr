---
title: Méthode relative (SQLServerResultSet) | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerResultSet.relative
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 2bcdbb69-95fd-4ae8-8488-1a75a91fe2e0
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f8e1c976ab8f89e18d6a86fb7d06a144a72dbe66
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="relative-method-sqlserverresultset"></a>Méthode relative (SQLServerResultSet)
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
  
 Toute tentative de déplacement au-delà de la première ou de la dernière ligne dans le jeu de résultats positionne le curseur avant ou après la première ou la dernière ligne. Appel de `relative(0)` est valide, mais ne modifie pas la position du curseur.  
  
 Appel de la méthode `relative(1)` est identique à l’appel du [suivant](../../../connect/jdbc/reference/next-method-sqlserverresultset.md) (méthode). Appel de la méthode `relative(-1)` est identique à l’appel du [précédente](../../../connect/jdbc/reference/previous-method-sqlserverresultset.md) (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
