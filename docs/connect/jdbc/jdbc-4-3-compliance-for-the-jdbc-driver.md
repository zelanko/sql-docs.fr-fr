---
title: JDBC 4.3 conformité pour le pilote JDBC | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 36025ec0-3c72-4e68-8083-58b38e42d03b
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f529c88044444f3fb6e428b6c69f5a5cf5917251
ms.sourcegitcommit: 6fa72c52c6d2256c5539cc16c407e1ea2eee9c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2018
ms.locfileid: "39278910"
---
# <a name="jdbc-43-compliance-for-the-jdbc-driver"></a>Conformité à JDBC 4.3 pour le pilote JDBC
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

    
> [!NOTE]  
>  Les versions antérieures à Microsoft JDBC Driver 6.4 pour SQL Server sont conformes aux spécifications de l'API Java Database Connectivity (JDBC) 4.2. Cette section ne s'applique pas aux versions antérieures à la version 6.4.  
  
 Depuis la version 6.4, Microsoft JDBC Driver pour SQL Server est 10 compatible de JAVA, mais il n’est pas entièrement conforme aux spécifications de JDBC API 4.3. Le pilote lève SQLFeatureNotSupportedException pour les méthodes non implémentées. 
 
 Les méthodes API JDBC 4.3 suivantes sont implémentées dans Microsoft JDBC Driver 6.4 pour SQL Server.
 
  **Classe SQLServerConnection**  
  
|Nouvelles méthodes|Description|Implémentation intéressante|  
|-----------------|-----------------|-------------------------------|  
|void beginRequest()|Indicateurs pour le pilote qu’une demande, une unité de travail, indépendante commence sur cette connexion. Pour plus d'informations, voir [java.sql.Connection](https://docs.oracle.com/javase/9/docs/api/java/sql/Connection.html#beginRequest--).|Enregistre les valeurs des champs de connexion qui sont modifiables par le biais des méthodes API publiques : `databaseAutoCommitMode`, `transactionIsolationLevel`, `networkTimeout`, `holdability`, `sendTimeAsDatetime`, `statementPoolingCacheSize`, `disableStatementPooling`, `serverPreparedStatementDiscardThreshold`, `enablePrepareOnFirstPreparedStatementCall `, `catalogName`, `sqlWarnings`, `useBulkCopyForBatchInsert `.|
|void endRequest()|Indicateurs pour le pilote d’une requête, une unité de travail, indépendante est terminée. Pour plus d'informations, voir [java.sql.Connection](https://docs.oracle.com/javase/9/docs/api/java/sql/Connection.html#endRequest--).|Ferme les instructions qui sont créées lors de l’unité de travail et restaure toutes les transactions ouvertes. La méthode rétablit également les modifications apportées aux champs de connexion qui sont répertoriés ci-dessus.|