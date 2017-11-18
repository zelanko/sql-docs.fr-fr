---
title: "Méthode getClientInfoProperties (SQLServerDatabaseMetaData) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: jdbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1568aef4-f4c4-40a0-a1ab-9c106905bd92
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 022f09c50d0a47851e375fcbb617ee40266dbb38
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="getclientinfoproperties-method-sqlserverdatabasemetadata"></a>Méthode getClientInfoProperties (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère une liste de propriétés d'informations clientes prises en charge par le pilote.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.ResultSet getClientInfoProperties()  
```  
  
## <a name="return-value"></a>Valeur retournée  
 Un objet de jeu de résultats.  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getClientInfoProperties est spécifiée par la méthode getClientInfoProperties dans l’interface java.sql.DatabaseMetaData.  
  
> [!NOTE]  
>  Cette méthode retourne un jeu de résultats vide. Le pilote prend en charge le paramètre exclusivement la **applicationName** et définit les **applicationName** uniquement au moment de la connexion. SQL Server ne prend pas en charge la mise à jour des informations d'application cliente une fois la connexion établie.  
  
## <a name="see-also"></a>Voir aussi  
 [Membres de SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  

