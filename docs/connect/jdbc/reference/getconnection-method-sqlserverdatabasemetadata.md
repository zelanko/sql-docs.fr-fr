---
title: Méthode getConnection (SQLServerDatabaseMetaData) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getConnection
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 16e46603-a678-4b0f-998e-479abbea151c
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7f56e236d957034be88897c3473877cb3414c0b3
ms.sourcegitcommit: fe5c45a492e19a320a1a36b037704bf132dffd51
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80923246"
---
# <a name="getconnection-method-sqlserverdatabasemetadata"></a>Méthode getConnection (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Récupère la connexion qui a produit cet objet de métadonnées.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public java.sql.Connection getConnection()  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Objet [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md).  
  
## <a name="exceptions"></a>Exceptions  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Notes  
 Cette méthode getConnection est spécifiée par la méthode getConnection de l’interface java.sql.DatabaseMetaData.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerDatabaseMetaData, méthodes](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData, membres](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData, classe](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
