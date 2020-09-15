---
description: Méthode setFetchSize (SQLServerStatement)
title: Méthode setFetchSize (SQLServerStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.setFetchSize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 760e555e-9667-4b40-b0ba-778026ff2923
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1f87aced668933da1e4bbde3b0f4d999abf7eac4
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88431841"
---
# <a name="setfetchsize-method-sqlserverstatement"></a>Méthode setFetchSize (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Donne un indicateur à [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] concernant le nombre de lignes à extraire de la base de données, lorsque davantage de lignes sont nécessaires.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public final void setFetchSize(int rows)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *rows*  
  
 **int** indiquant le nombre de lignes à récupérer (fetch).  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode setFetchSize est spécifiée par la méthode setFetchSize de l’interface java.sql.Statement.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerStatement, membres](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
