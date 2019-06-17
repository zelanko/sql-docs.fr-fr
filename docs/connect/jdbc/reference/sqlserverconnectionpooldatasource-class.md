---
title: Classe SQLServerConnectionPoolDataSource | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b00e5a90-2af7-4d04-8ef8-256183777dcf
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: f80991eaf3449412db672dfcb73f71c596d1bb29
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66800620"
---
# <a name="sqlserverconnectionpooldatasource-class"></a>Classe SQLServerConnectionPoolDataSource
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  Représente des connexions de bases de données physiques pour les gestionnaires de regroupement de connexions.  
  
 **Package :** com.microsoft.sqlserver.jdbc  
  
 **Étend :** [SQLServerDataSource](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
 **Implémente :** javax.sql.ConnectionPoolDataSource  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
public class SQLServerConnectionPoolDataSource  
```  
  
## <a name="remarks"></a>Notes  
 SQLServerConnectionPoolDataSource est généralement utilisé dans les environnements de serveur d’applications Java qui prennent en charge le regroupement de connexions intégré et ont besoin de ConnectionPoolDataSource pour les connexions physiques : par exemple, les serveurs d’applications Java Platform, Enterprise Edition (Java EE) qui offrent un regroupement de connexions spécifique des API JDBC 3.0.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLServerConnectionPoolDataSource, membres](../../../connect/jdbc/reference/sqlserverconnectionpooldatasource-members.md)   
 [Informations de référence sur l'API du pilote JDBC](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
