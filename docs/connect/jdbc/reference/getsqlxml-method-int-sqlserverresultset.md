---
description: Méthode getSQLXML (int) (SQLServerResultSet)
title: Méthode getSQLXML (int) (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: faa35676-573d-48d5-afd9-850134735728
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c92b53d1a996d6ecab8d3a13ffb862b921a70131
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88434481"
---
# <a name="getsqlxml-method-int-sqlserverresultset"></a>Méthode getSQLXML (int) (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la valeur d’une colonne désignée dans la ligne actuelle de l’objet [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) sous forme d’objet SQLXML.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final java.sql.SQLXML getSQLXML(int columnIndex)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *columnIndex*  
  
 **int** indiquant l’index de la colonne.  
  
## <a name="return-value"></a>Valeur de retour  
 ASQLXMLobject.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getSQLXML est spécifiée par la méthode getSQLXML de l’interface java.sql.ResultSet.  
  
## <a name="see-also"></a>Voir aussi  
 [getSQLXML, méthode &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getsqlxml-method-sqlserverresultset.md)   
 [Membres de SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-members.md)  
  
  
