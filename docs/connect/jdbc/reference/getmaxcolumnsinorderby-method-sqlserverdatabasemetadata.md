---
title: Méthode getMaxColumnsInOrderBy (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getMaxColumnsInOrderBy
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: d6af9bb4-c55d-41f4-a266-d10ebee61194
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d5b18cd04bd9d3569e45780ff54d122689e58a14
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80907084"
---
# <a name="getmaxcolumnsinorderby-method-sqlserverdatabasemetadata"></a>Méthode getMaxColumnsInOrderBy (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère le nombre maximal de colonnes autorisé par cette base de données dans une clause ORDER BY.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int getMaxColumnsInOrderBy()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **int** indiquant le nombre maximal de colonnes autorisé.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getMaxColumnsInOrderBy est spécifiée par la méthode getMaxColumnsInOrderBy de l’interface java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
