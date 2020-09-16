---
description: Méthode getMaxProcedureNameLength (SQLServerDatabaseMetaData)
title: Méthode getMaxProcedureNameLength (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getMaxProcedureNameLength
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e1c05eb3-8465-46fd-99bc-5e8effcafee5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 05a3737d1d589d68bc98b8625b510a257651ff75
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88435541"
---
# <a name="getmaxprocedurenamelength-method-sqlserverdatabasemetadata"></a>Méthode getMaxProcedureNameLength (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère le nombre maximal de caractères autorisé par cette base de données dans un nom de procédure.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public int getMaxProcedureNameLength()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 **int** indiquant le nombre maximal de caractères autorisé.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getMaxProcedureNameLength est spécifiée par la méthode getMaxProcedureNameLength de l’interface java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
