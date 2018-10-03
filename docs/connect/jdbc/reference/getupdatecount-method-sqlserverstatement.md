---
title: getUpdateCount, méthode (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getUpdateCount
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e9570228-4500-44b6-b2f1-84ac050b5112
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7c4dadcaa4bfb0c2bf4698cf7b4e0be02a7d4ccf
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47633737"
---
# <a name="getupdatecount-method-sqlserverstatement"></a>getUpdateCount, méthode (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère le résultat actuel en tant que nombre de mises à jour.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final int getUpdateCount()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Un **int** qui contient le nombre de mises à jour. Si le résultat retourné est un objet de jeu de résultats ou s'il n'y a plus de résultat, -1 est retourné.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode getUpdateCount est spécifiée par la méthode getUpdateCount dans l’interface java.sql.Statement.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerStatement, membres](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
