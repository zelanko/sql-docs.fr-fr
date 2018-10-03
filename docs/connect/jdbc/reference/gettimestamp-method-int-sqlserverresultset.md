---
title: getTimestamp, méthode (int) (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getTimestamp (int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ad538a76-983f-4175-9481-9e7fa9480c71
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 286156070f62faa576eec11cb1f6d946420c7fb6
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47823287"
---
# <a name="gettimestamp-method-int-sqlserverresultset"></a>getTimestamp, méthode (int) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur de l’index de la colonne désignée dans la ligne actuelle de cet objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) en tant qu’objet java.sql.Timestamp dans le langage de programmation Java.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.Timestamp getTimestamp(int columnIndex)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *columnIndex*  
  
 Un **int** qui indique l’index de colonne.  
  
## <a name="return-value"></a>Valeur retournée  
 Objet Timestamp.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode getTimestamp est spécifiée par la méthode getTimestamp dans l’interface java.sql.ResultSet.  
  
 Cette méthode retourne des valeurs seulement à partir des colonnes datetime et smalldatetime de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
## <a name="see-also"></a> Voir aussi  
 [getTimestamp, méthode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/gettimestamp-method-sqlserverresultset.md)   
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
