---
title: setfetchdirection, méthode (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.setFetchDirection
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 4ee82290-508d-4bff-a5c5-8a56338deef8
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 31315b70f770d2f95e97d34b2064152234cae248
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66803394"
---
# <a name="setfetchdirection-method-sqlserverresultset"></a>Méthode setFetchDirection (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Fournit un conseil concernant la direction de traitement des lignes de cet objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md).  
  
> [!NOTE]  
>  Actuellement, cette méthode n’est pas prise en charge par le [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)]. Si vous utilisez cette méthode, le pilote JDBC mémorise le paramètre, mais actuellement il n'intervient pas dessus.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void setFetchDirection(int direction)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *direction*  
  
 Un **int** qui indique la direction d’extraction suggérée. Il peut s'agir de l'une des valeurs suivantes :  
  
 ResultSet.FETCH_FORWARD  
  
 ResultSet.FETCH_REVERSE  
  
 ResultSet.FETCH_UNKNOWN  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setFetchDirection est spécifiée par la méthode setFetchDirection dans l’interface java.sql.ResultSet.  
  
 La valeur initiale de cette méthode est déterminée par l’objet [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) qui a produit cet objet SQLServerResultSet. La direction d'extraction peut être modifiée à tout moment.  
  
> [!NOTE]  
>  L'utilisation de cette méthode lorsque le type de curseur est avant uniquement est sans effet.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
