---
title: Méthode supportsSelectForUpdate (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsSelectForUpdate
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 721bc8e3-36c0-4fa6-8561-4f8d54c8265a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a5b70b18a7b331ac448d5135d57e95741f76b85b
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "67968864"
---
# <a name="supportsselectforupdate-method-sqlserverdatabasemetadata"></a>Méthode supportsSelectForUpdate (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère les informations déterminant si cette base de données prend en charge les instructions SELECT FOR UPDATE.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean supportsSelectForUpdate()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **true** en cas de prise en charge. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode supportsSelectForUpdate est spécifiée par la méthode supportsSelectForUpdate de l’interface java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
