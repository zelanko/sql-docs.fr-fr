---
title: Méthode supportsCatalogsInTableDefinitions | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsCatalogsInTableDefinitions
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 1e1e50ac-f3d4-416a-8a69-d8b7b4f30bf3
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8c57bf4585c621093acf2ba41d7e12bd44be4557
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47616961"
---
# <a name="supportscatalogsintabledefinitions-method-sqlserverdatabasemetadata"></a>Méthode supportsCatalogsInTableDefinitions (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère les informations déterminant si un nom de catalogue peut être utilisé dans une instruction de définition de table.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean supportsCatalogsInTableDefinitions()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si pris en charge. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode supportsCatalogsInTableDefinitions est spécifiée par la méthode supportsCatalogsInTableDefinitions dans l’interface java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
