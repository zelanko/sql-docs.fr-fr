---
title: Méthode setFetchDirection (SQLServerResultSet) | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: jdbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerResultSet.setFetchDirection
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4ee82290-508d-4bff-a5c5-8a56338deef8
caps.latest.revision: 12
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2c52272d3bceb80993420b13846d8357b2fed1a0
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="setfetchdirection-method-sqlserverresultset"></a>Méthode setFetchDirection (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Fournit un Conseil concernant la direction dans laquelle les lignes dans cette [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) objet est traité.  
  
> [!NOTE]  
>  Cette méthode n’est pas actuellement pris en charge par le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]. Si vous utilisez cette méthode, le pilote JDBC mémorise le paramètre, mais actuellement il n'intervient pas dessus.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setFetchDirection(int direction)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Direction*  
  
 Un **int** qui indique la direction d’extraction suggérée. Il peut s'agir de l'une des valeurs suivantes :  
  
 ResultSet.FETCH_FORWARD  
  
 ResultSet.FETCH_REVERSE  
  
 ResultSet.FETCH_UNKNOWN  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setFetchDirection est spécifiée par la méthode setFetchDirection dans l’interface java.sql.ResultSet.  
  
 La valeur initiale de cette méthode est déterminée par le [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) objet qui a produit cet objet SQLServerResultSet. La direction d'extraction peut être modifiée à tout moment.  
  
> [!NOTE]  
>  L'utilisation de cette méthode lorsque le type de curseur est avant uniquement est sans effet.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
