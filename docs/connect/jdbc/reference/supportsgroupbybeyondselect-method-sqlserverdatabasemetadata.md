---
description: Méthode supportsGroupByBeyondSelect (SQLServerDatabaseMetaData)
title: Méthode supportsGroupByBeyondSelect (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.supportsGroupByBeyondSelect
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: eadd2c37-d9ec-4b47-a91e-ed90b1eaf4b4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: df5107683e6bc9b80c97fcf111c63eb4caceb7c0
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88462446"
---
# <a name="supportsgroupbybeyondselect-method-sqlserverdatabasemetadata"></a>Méthode supportsGroupByBeyondSelect (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère les informations déterminant si cette base de données prend en charge l'utilisation de colonnes non incluses dans l'instruction SELECT d'une clause GROUP BY à condition que toutes les colonnes de l'instruction SELECT soient incluses dans la clause GROUP BY.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public boolean supportsGroupByBeyondSelect()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **true** en cas de prise en charge. Dans le cas contraire, la valeur est **false**.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode supportsGroupByBeyondSelect est spécifiée par la méthode supportsGroupByBeyondSelect de l’interface java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
