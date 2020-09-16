---
description: Méthode supportsANSI92EntryLevelSQL (SQLServerDatabaseMetaData)
title: Méthode supportsANSI92EntryLevelSQL (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsANSI92EntryLevelSQL
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: a3fffc08-7254-4af7-bbae-8ff591fbd5ec
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ed62c28bfd0017e96ca90e9b62189588b01aad7b
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88472081"
---
# <a name="supportsansi92entrylevelsql-method-sqlserverdatabasemetadata"></a>Méthode supportsANSI92EntryLevelSQL (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère les informations déterminant si cette base de données prend en charge la grammaire SQL de niveau d'entrée ANSI92.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean supportsANSI92EntryLevelSQL()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **true** en cas de prise en charge. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode supportsANSI92EntryLevelSQL est spécifiée par la méthode supportsANSI92EntryLevelSQL de l’interface java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
