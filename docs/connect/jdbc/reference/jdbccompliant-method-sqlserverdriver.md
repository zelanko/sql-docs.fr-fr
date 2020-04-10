---
title: Méthode jdbcCompliant (SQLServerDriver) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDriver.jdbcCompliant
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b299b20d-d1cd-45b3-91dc-dcf579498570
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3ae5ac88d0427a605493bc19786bdd5f23dc93b6
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80915061"
---
# <a name="jdbccompliant-method-sqlserverdriver"></a>Méthode jdbcCompliant (SQLServerDriver)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Vérifie si [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] est conforme à la spécification JDBC.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean jdbcCompliant()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **true** si le pilote JDBC respecte la configuration requise. Dans le cas contraire, la valeur est **false**.  
  
## <a name="remarks"></a>Notes  
 Cette méthode jdbcCompliant est spécifiée par la méthode jdbcCompliant de l’interface java.sql.Driver.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDriver, méthodes](../../../connect/jdbc/reference/sqlserverdriver-methods.md)   
 [SQLServerDriver, membres](../../../connect/jdbc/reference/sqlserverdriver-members.md)   
 [SQLServerDriver, classe](../../../connect/jdbc/reference/sqlserverdriver-class.md)  
  
  
