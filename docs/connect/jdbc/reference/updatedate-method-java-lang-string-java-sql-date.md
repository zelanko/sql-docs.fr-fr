---
title: updateDate, méthode (java.lang.String, java.sql.Date) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateDate (java.lang.String, java.sql.Date)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4fbe9123-7365-4a8f-bbd5-dc2b16f1b231
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2eee4ccb8230ee32398cb75445297950ff89aa94
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67999145"
---
# <a name="updatedate-method-javalangstring-javasqldate"></a>Méthode updateDate (java.lang.String, java.sql.Date)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Met à jour la colonne désignée avec une valeur de date en fonction du nom de colonne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void updateDate(java.lang.String columnName,  
                       java.sql.Date x)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *columnName*  
  
 Valeur **String** qui contient le nom de la colonne.  
  
 *x*  
  
 Valeur de date.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode updateDate est spécifiée par la méthode updateDate de l’interface java.sql.ResultSet.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthode updateDate &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatedate-method-sqlserverresultset.md)   
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
