---
title: Méthode getConcurrency (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getConcurrency
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 207e25f4-769c-4ff3-913c-3517b06208e4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5d0d59186e15dc07d1d4e91ac673c456ec592d01
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2020
ms.locfileid: "67952825"
---
# <a name="getconcurrency-method-sqlserverresultset"></a>getConcurrency, méthode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère le mode de concurrence de cet objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int getConcurrency()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **int** indiquant le type de concurrence, qui peut être l'une des valeurs suivantes :  
  
 ResultSet.CONCUR_READ_ONLY  
  
 ResultSet.CONCUR_UPDATABLE  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getConcurrency est spécifiée par la méthode getConcurrency de l’interfacejava.sql.ResultSet.  
  
 La concurrence utilisée est déterminée par l’objet [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) qui a créé le jeu de résultats.  
  
 Cette méthode permet de déterminer la concurrence réelle. Si l'application a sélectionné CONCUR_READ_ONLY ou CONCUR_UPDATABLE, ces options seront retournées. Si l'application a utilisé la concurrence par défaut, c'est CONCUR_READ_ONLY qui est retourné.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
