---
title: Méthode getRowIdLifetime (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 317c0b44-fe3f-4142-9cab-e40e4c4fe070
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 65541bc857dfcdd7c55caa8e2e7d3831026c79e4
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47731517"
---
# <a name="getrowidlifetime-method-sqlserverdatabasemetadata"></a>Méthode getRowIdLifetime (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Retourne un statut indiquant si le type de données SQL RowId est pris en charge ou non. S'il l'est, il retourne la durée de validité d'un objet RowId.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.RowIdLifetime getRowIdLifetime()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Un objet RowIdLifetime.  
  
> [!NOTE]  
>  Dans la pilote JDBC version 2.0, cette méthode retourne la valeur de java.sql.RowIdLifetime.ROWID_UNSUPPORTED.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes   
 Cette méthode getRowIdLifetime est spécifiée par la méthode getRowIdLifetime dans l’interface java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a> Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
