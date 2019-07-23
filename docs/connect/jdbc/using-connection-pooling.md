---
title: Utilisation du regroupement de connexions | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 699d4e8a-34bf-4c60-b0d5-4a10dad6084a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ec9d1717d12624ffa7663479f1d98146aea1137f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "67916334"
---
# <a name="using-connection-pooling"></a>Utilisation d'un regroupement de connexions

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] prend en charge le regroupement de connexions Java EE (Java Platform, Enterprise Edition). Le pilote JDBC implémente les interfaces JDBC 3.0 requises pour permettre au pilote de participer aux implémentations de regroupements de connexions fournies par des fournisseurs d'intergiciels (middleware) et compatibles JDBC 3.0. Des intergiciels (middleware) tels que des serveurs d'applications Java EE offrent souvent des fonctionnalités de regroupement de connexions compatibles. Le pilote JDBC prendra part à des connexions regroupées dans ces environnements.  
  
> [!NOTE]  
> Même si le pilote JDBC prend en charge le regroupement de connexions Java EE, il ne fournit pas sa propre implémentation de regroupement. Le pilote recourt à des serveurs d'applications Java tiers pour gérer les connexions.  
  
## <a name="remarks"></a>Notes

Les classes pour l'implémentation du regroupement de connexions sont les suivantes.  
  
| Classe                                                           | Implémentations                                                    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| --------------------------------------------------------------- | ------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| com.microsoft.sqlserver.jdbc. SQLServerXADataSource             | javax.sql.ConnectionPoolDataSource et javax.sql.XADataSource | Nous vous recommandons d’utiliser la classe [SQLServerXADataSource](../../connect/jdbc/reference/sqlserverxadatasource-class.md) pour tous les besoins de serveur Java EE, car elle implémente l’ensemble des regroupements JDBC 3.0 et des interfaces XA.                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| com.microsoft.sqlserver.jdbc. SQLServerConnectionPoolDataSource | javax.sql.ConnectionPoolDataSource                            | Cette classe est une fabrique de connexions qui permet au serveur d'applications Java EE de peupler son regroupement de connexions à l'aide de connexions physiques. Si la configuration du fournisseur de Java EE nécessite une classe implémentant javax.sql.ConnectionPoolDataSource, définissez le nom de classe comme [SQLServerConnectionPoolDataSource](../../connect/jdbc/reference/sqlserverconnectionpooldatasource-class.md). En règle générale, nous vous recommandons d’utiliser plutôt la classe [SQLServerXADataSource](../../connect/jdbc/reference/sqlserverxadatasource-class.md), car elle implémente le regroupement et les interfaces XA ; de plus, elle a été vérifiée dans davantage de configurations de serveur Java EE. |
  
 Le code d'application JDBC doit toujours fermer les connexions de façon explicite afin de profiter au maximum du regroupement. Si l'application ferme explicitement une connexion, l'implémentation du regroupement peut réutiliser la connexion immédiatement. Si la connexion n'est pas fermée, d'autres applications ne peuvent pas la réutiliser. Des applications peuvent utiliser la construction `finally` pour s’assurer que les connexions regroupées sont fermées même en cas d’exception.  
  
> [!NOTE]  
> Le pilote JDBC n'appelle pas actuellement la procédure stockée sp_reset_connection lorsqu'il retourne la connexion au regroupement. Au lieu de cela, le pilote recourt à des serveurs d'applications Java tiers pour rétablir les connexions à leur état original.  
  
## <a name="see-also"></a>Voir aussi

[Connexion à SQL Server avec le pilote JDBC](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)  
