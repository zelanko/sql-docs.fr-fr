---
title: "Méthode getCatalogTerm (SQLServerDatabaseMetaData) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- SQLServerDatabaseMetaData.getCatalogTerm
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 0aa5d372-16aa-4790-a8f6-f8b742798f8f
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 2195081eb25174092c195ac8bcfd1878c545cd8b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="getcatalogterm-method-sqlserverdatabasemetadata"></a>méthode getCatalogTerm (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère le terme favori du fournisseur de base de données pour « catalog ».  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.lang.String getCatalogTerm()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 A **chaîne** qui contient le terme catalogue.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getCatalogTerm est spécifiée par la méthode getCatalogTerm dans l’interface java.sql.DatabaseMetaData.  
  
 Lorsque vous utilisez la [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] avec un [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] base de données, cette méthode retourne le terme « database ».  
  
## <a name="see-also"></a>Voir aussi  
 [Méthodes SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [Membres de SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

