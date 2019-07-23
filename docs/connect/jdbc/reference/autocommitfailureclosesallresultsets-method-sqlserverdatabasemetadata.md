---
title: Le pilote JDBC ferme-t-il les jeux de résultats ouverts | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 1739ecb5-e5cb-4807-b5a8-97c0299929d0
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 9fded722f558b68e393fc4e0815a35cc7383b8d6
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67955855"
---
# <a name="autocommitfailureclosesallresultsets-method-sqlserverdatabasemetadata"></a>Méthode autoCommitFailureClosesAllResultSets (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Indique si le pilote JDBC ferme tous les jeux de résultats ouverts, notamment ceux pouvant être mis en attente, lorsqu'une validation automatique est activée et une exception levée.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean autoCommitFailureClosesAllResultSets()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si tous les jeux de résultats ouverts, y compris ceux qui peuvent être débloqués, sont fermés lorsqu’une validation automatique est activée et qu’une exception est levée. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode autoCommitFailureClosesAllResultSets est spécifiée par la méthode autoCommitFailureClosesAllResultSets dans l’interface java. Sql. DatabaseMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
