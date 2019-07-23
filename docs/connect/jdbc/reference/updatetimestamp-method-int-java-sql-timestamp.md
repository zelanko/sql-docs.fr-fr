---
title: updateTimestamp, méthode (int, java.sql.Timestamp) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateTimestamp (int, java.sql.Timestamp)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: db83d9d7-137b-4a28-a2ca-d4782e0a256e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 00e170e0366d5ed785a4b27053f3805c13f2c54c
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67998156"
---
# <a name="updatetimestamp-method-int-javasqltimestamp"></a>Méthode updateTimestamp (int, java.sql.Timestamp)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Met à jour la colonne désignée avec une valeur d'horodateur en fonction de l'index de colonne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void updateTimestamp(int index,  
                            java.sql.Timestamp x)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *index*  
  
 **Entier** qui indique l’index de colonne.  
  
 *x*  
  
 Valeur d’horodateur.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode updateTimestamp est spécifiée par la méthode updateTimestamp dans l’interface java. Sql. ResultSet.  
  
## <a name="see-also"></a>Voir aussi  
 [updateTimestamp, méthode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updatetimestamp-method-sqlserverresultset.md)   
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
