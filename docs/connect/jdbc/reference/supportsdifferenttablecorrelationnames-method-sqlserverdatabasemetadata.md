---
title: Méthode supportsDifferentTableCorrelationNames | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsDifferentTableCorrelationNames
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: b4f8db0c-2eaf-476b-b916-3e83355778f7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e8909296b03c6c9e8f167704b76f025ab8a8aca8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47646637"
---
# <a name="supportsdifferenttablecorrelationnames-method-sqlserverdatabasemetadata"></a>Méthode supportsDifferentTableCorrelationNames (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère les informations déterminant si les noms de corrélation de tables, lorsqu'ils sont pris en charge, doivent être différents des noms des tables.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean supportsDifferentTableCorrelationNames()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si pris en charge. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode supportsDifferentTableCorrelationNames est spécifiée par la méthode supportsDifferentTableCorrelationNames dans l’interface java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
