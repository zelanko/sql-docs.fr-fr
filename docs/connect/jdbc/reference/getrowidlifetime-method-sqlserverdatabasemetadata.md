---
description: Méthode getRowIdLifetime (SQLServerDatabaseMetaData)
title: Méthode getRowIdLifetime (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 317c0b44-fe3f-4142-9cab-e40e4c4fe070
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c67c88abc02faccc1b6a4e391eee674e7d99112f
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88434711"
---
# <a name="getrowidlifetime-method-sqlserverdatabasemetadata"></a>Méthode getRowIdLifetime (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne un statut indiquant si le type de données SQL RowId est pris en charge ou non. S'il l'est, il retourne la durée de validité d'un objet RowId.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.RowIdLifetime getRowIdLifetime()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Objet RowIdLifetime.  
  
> [!NOTE]  
>  Dans la version 2.0 du pilote JDBC, cette méthode retourne la valeur java.sql.RowIdLifetime.ROWID_UNSUPPORTED.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getRowIdLifetime est spécifiée par la méthode getRowIdLifetime de l’interface java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
