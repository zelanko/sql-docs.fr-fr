---
title: Méthode getFetchDirection (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getFetchDirection
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5ab385c2-e18c-4b75-ac2d-2402af5c52a5
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f56893764392236d563fa2b9a236f55e67e13595
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67983246"
---
# <a name="getfetchdirection-method-sqlserverresultset"></a>getFetchDirection, méthode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la direction d’extraction pour cet objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int getFetchDirection()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 **Entier** qui indique le sens d’extraction actuel.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getFetchDirection est spécifiée par la méthode getFetchDirection dans l’interface java. Sql. ResultSet.  
  
 Cette méthode retourne FETCH_FORWARD pour les curseurs avant uniquement, le dernier paramètre défini par l’appel de la méthode [setFetchDirection](../../../connect/jdbc/reference/setfetchdirection-method-sqlserverresultset.md) pour d’autres types de curseurs, et retourne FETCH_UNKNOWN pour ces types de curseurs si la méthode setFetchDirection n’a jamais été appelée.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
