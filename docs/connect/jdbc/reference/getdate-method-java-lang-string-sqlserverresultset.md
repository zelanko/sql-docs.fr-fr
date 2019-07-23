---
title: getDate, méthode (Java. lang. String) Column | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getDate (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 821058ae-cbe3-4a14-aa02-d55e45491437
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c534c043de11d9123beaaa36f38c4bbd009012c9
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67983913"
---
# <a name="getdate-method-javalangstring-sqlserverresultset"></a>getDate, méthode (java.lang.String) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur du nom de la colonne désignée dans la ligne actuelle de cet objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) en tant qu’objet java.sql.Date dans le langage de programmation Java.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.Date getDate(java.lang.String columnName)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *columnName*  
  
 Valeur **String** qui contient le nom de la colonne.  
  
## <a name="return-value"></a>Valeur retournée  
 Objet date.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getDate est spécifiée par la méthode getDate de l’interface java.sql.ResultSet.  
  
 Cette méthode retourne une partie date valide d’un type de données [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] datetime ou smalldatetime, avec la partie heure définie sur l’heure de référence Java 00:00 (minuit).  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode getDate &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getdate-method-sqlserverresultset.md)   
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
