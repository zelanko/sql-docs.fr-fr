---
description: getConcurrency, méthode (SQLServerResultSet)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b8cb92a019c9c65e867be023fab9bc299a7a8bc8
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88436551"
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
  
  
