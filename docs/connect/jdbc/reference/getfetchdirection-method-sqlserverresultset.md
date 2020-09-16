---
description: getFetchDirection, méthode (SQLServerResultSet)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 50b0ec2751f2a6cabe852be3e8610b3a97328c13
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88436051"
---
# <a name="getfetchdirection-method-sqlserverresultset"></a>getFetchDirection, méthode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la direction d’extraction pour cet objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int getFetchDirection()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **int** indiquant le sens d’extraction actuel.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getFetchDirection est spécifiée par la méthode getFetchDirection de l’interface java.sql.ResultSet.  
  
 Cette méthode retourne FETCH_FORWARD pour les curseurs avant uniquement, le dernier paramètre défini par l’appel de la méthode [setFetchDirection](../../../connect/jdbc/reference/setfetchdirection-method-sqlserverresultset.md) pour d’autres types de curseurs, et retourne FETCH_UNKNOWN pour ces types de curseurs si la méthode setFetchDirection n’a jamais été appelée.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
