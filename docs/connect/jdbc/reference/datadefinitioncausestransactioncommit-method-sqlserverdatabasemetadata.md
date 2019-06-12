---
title: Transaction de Force d’instruction de définition de données valide. | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.dataDefinitionCausesTransactionCommit
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: bf04fa73-b9f1-4403-b6a0-e53d0d27c671
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 15c99e0ba9c94306029e67080f7cb6a26b44b9ab
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66772826"
---
# <a name="datadefinitioncausestransactioncommit-method-sqlserverdatabasemetadata"></a>Méthode dataDefinitionCausesTransactionCommit (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère les informations déterminant si une instruction de définition des données dans une transaction force la transaction à valider.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean dataDefinitionCausesTransactionCommit()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si l’instruction DDL impose une validation. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode dataDefinitionCausesTransactionCommit est spécifiée par la méthode dataDefinitionCausesTransactionCommit dans l’interface java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
