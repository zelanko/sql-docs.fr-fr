---
title: setFetchSize, méthode (SQLServerStatement) | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ed9b715748afbbde4dc58fcd4df9c96b4011d944
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47605627"
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
  
 Un **int** qui indique le nombre de lignes à extraire.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode setFetchSize est spécifiée par la méthode setFetchSize de l’interface java.sql.Statement.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerStatement, membres](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement, classe](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
