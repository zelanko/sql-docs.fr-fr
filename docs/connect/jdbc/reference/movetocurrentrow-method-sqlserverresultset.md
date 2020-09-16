---
description: moveToCurrentRow, méthode (SQLServerResultSet)
title: Méthode moveToCurrentRow (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.moveToCurrentRow
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 9a7c754c-2d72-4207-b3bd-2afc6047fb3d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7c5b26d92a64c8c9bfa952ac04a3a924c987d5f3
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88433191"
---
# <a name="movetocurrentrow-method-sqlserverresultset"></a>moveToCurrentRow, méthode (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Déplace le curseur à la position de curseur mémorisée, qui est généralement la ligne actuelle.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void moveToCurrentRow()  
```  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode moveToCurrentRow est spécifiée par la méthode moveToCurrentRow de l’interface java.sql.ResultSet.  
  
 Cette méthode n'a aucun effet si le curseur ne se trouve pas sur la ligne d'insertion.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerResultSet, membres](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet, classe](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
