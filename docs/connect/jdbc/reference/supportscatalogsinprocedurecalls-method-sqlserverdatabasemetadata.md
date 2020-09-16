---
description: Méthode supportsCatalogsInProcedureCalls (SQLServerDatabaseMetaData)
title: Méthode supportsCatalogsInProcedureCalls | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsCatalogsInProcedureCalls
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5ec3571a-c7c6-4b94-a9ea-ac08adc7f978
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e5d4a800e7a62728457c09083f8dfa57edc22cf1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88467053"
---
# <a name="supportscatalogsinprocedurecalls-method-sqlserverdatabasemetadata"></a>Méthode supportsCatalogsInProcedureCalls (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère les informations déterminant si un nom de catalogue peut être utilisé dans une instruction d'appel de procédure.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean supportsCatalogsInProcedureCalls()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **true** en cas de prise en charge. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode supportsCatalogsInProcedureCalls est spécifiée par la méthode supportsCatalogsInProcedureCalls dans l’interface java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
