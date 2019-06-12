---
title: Méthode supportsIntegrityEnhancementFacility | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsIntegrityEnhancementFacility
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: edee084b-9a8c-4167-9e13-66fc3ed1ecaa
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 1e841d3b6999d6852dc9b792fb55ffdd94195e3a
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66764285"
---
# <a name="supportsintegrityenhancementfacility-method-sqlserverdatabasemetadata"></a>Méthode supportsIntegrityEnhancementFacility (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère les informations déterminant si cette base de données prend en charge SQL Integrity Enhancement Facility.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean supportsIntegrityEnhancementFacility()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 **true** si pris en charge. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode supportsIntegrityEnhancementFacility est spécifiée par la méthode supportsIntegrityEnhancementFacility dans l’interface java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
