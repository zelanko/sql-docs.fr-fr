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
ms.openlocfilehash: fb880b72e7ef6dc3a03beba28d3ae9b3ca7d3c44
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67999234"
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
  
 **int** indiquant l’index de la colonne.  
  
 *clobValue*  
  
 Objet Clob.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode updateClob est spécifiée par la méthode updateClob de l’interface java.sql.ResultSet.  
  
## <a name="see-also"></a>Voir aussi  
 [updateClob, méthode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updateclob-method-sqlserverresultset.md)   
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
