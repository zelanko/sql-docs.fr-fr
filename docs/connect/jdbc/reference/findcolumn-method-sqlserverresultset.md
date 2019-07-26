---
title: Méthode findColumn (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.findColumn
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 7c29994a-0b53-420b-8a9b-82a9eef08587
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 24aed500f5b345e2ba3762bdd7a888fc5f8f31ba
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67954571"
---
# <a name="findcolumn-method-sqlserverresultset"></a>findColumn, méthode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère l’index de la première colonne correspondant au nom de colonne donné dans cet objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int findColumn(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *columnName*  
  
 **String** contenant le nom de la colonne.  
  
## <a name="return-value"></a>Valeur retournée  
 **Entier** qui indique l’index de colonne.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode findColumn est spécifiée par la méthode findColumn dans l’interface java. Sql. ResultSet.  
  
 Si plusieurs colonnes portent le même nom, la méthode findColumn retourne la première correspondance respectant la casse. En l'absence de correspondance respectant la casse, cette méthode retourne la première correspondance ne respectant pas la casse.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
