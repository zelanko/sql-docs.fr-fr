---
description: Classe SQLServerConnectionPoolDataSource
title: Classe SQLServerConnectionPoolDataSource | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b00e5a90-2af7-4d04-8ef8-256183777dcf
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2faa9b4df512d9b37bbba581353938120b85cbb1
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88354785"
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
  
  
