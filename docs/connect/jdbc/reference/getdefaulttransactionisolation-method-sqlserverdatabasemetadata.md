---
title: "Méthode getDefaultTransactionIsolation (SQLServerDatabaseMetaData) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname: SQLServerDatabaseMetaData.getDefaultTransactionIsolation
apilocation: sqljdbc.jar
apitype: Assembly
ms.assetid: 85b867ed-de5a-4879-b3f8-bce897879077
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 09cece0ac8bdf7ed1ac3dfddf38d723c36368132
ms.sourcegitcommit: 2713f8e7b504101f9298a0706bacd84bf2eaa174
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="getdefaulttransactionisolation-method-sqlserverdatabasemetadata"></a>Méthode getDefaultTransactionIsolation (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère le niveau d'isolation de la transaction par défaut pour cette base de données.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int getDefaultTransactionIsolation()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Un **int** qui indique le niveau d’isolation de transaction par défaut.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getDefaultTransactionIsolation est spécifiée par la méthode getDefaultTransactionIsolation dans l’interface java.sql.DatabaseMetaData.  
  
 Lorsque vous utilisez la [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] avec un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] base de données, cette méthode retourne une valeur de TRANSACTION_READ_COMMITTED, ou le **int** valeur 2.  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membres de SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
