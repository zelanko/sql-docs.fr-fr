---
title: Méthode updateClob (int, java.sql.Clob) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateClob (int, java.sql.Clob)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: d2a5e9cb-2631-4f6e-a90c-4bee58e2f7b8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: adc082cfca814b8f10630fe7b4436b87da13ffc8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47596718"
---
# <a name="updateclob-method-int-javasqlclob"></a>Méthode updateClob (int, java.sql.Clob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Met à jour la colonne désignée avec une valeur java.sql.Clob en fonction de l'index de colonne.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void updateClob(int columnIndex,  
                       java.sql.Clob clobValue)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *columnIndex*  
  
 Un **int** qui indique l’index de colonne.  
  
 *clobValue*  
  
 Un objet Clob.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode updateClob est spécifiée par la méthode updateClob dans l’interface java.sql.ResultSet.  
  
## <a name="see-also"></a> Voir aussi  
 [updateClob, méthode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updateclob-method-sqlserverresultset.md)   
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
