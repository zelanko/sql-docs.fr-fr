---
title: close, méthode (SQLServerPreparedStatement) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.close
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 36db9ff7-5819-4827-9803-4a81c99069b3
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: a414562a8ed400e3d667e304924b0487a5176891
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66786744"
---
# <a name="close-method-sqlserverpreparedstatement"></a>close, méthode (SQLServerPreparedStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Libère immédiatement les ressources JDBC et la base de données de cet objet Statement, au lieu de patienter jusqu’à leur libération automatique.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public void close()  
```  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode close est spécifiée par la méthode close de l’interface java.sql.Statement.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerPreparedStatement, membres](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement, classe](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
