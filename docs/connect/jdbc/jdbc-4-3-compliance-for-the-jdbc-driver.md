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
ms.openlocfilehash: 44ec3198bfb6f9898406688df2544dd2e243294b
ms.sourcegitcommit: e02c28b0b59531bb2e4f361d7f4950b21904fb74
ms.translationtype: MTE75
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39459483"
---
# <a name="jdbc-43-compliance-for-the-jdbc-driver"></a>Conformité à JDBC 4.3 pour le pilote JDBC

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

> [!NOTE]  
> Les versions antérieures à Microsoft JDBC Driver 6.4 pour SQL Server sont conformes uniquement aux spécifications de l’API Java Database Connectivity (JDBC) 4.2. Cette section ne s’applique pas aux versions qui contiennent la version 6.4 et antérieures à celle-ci.

Depuis la version 6.4, Microsoft JDBC Driver pour SQL Server JAVA 9 n’est compatible et lève `SQLFeatureNotSupportedException` pour les nouvelles API 4.3 JDBC qui ont non implémenté des méthodes.

Microsoft JDBC Driver 7.0 relatives à la version de SQL Server, le pilote est désormais JAVA 10 compatible, et prend en charge ci-dessous mentionné API. Le pilote lève `SQLFeatureNotSupportedException` pour d’autres méthodes non implémentées à partir de spécifications de JDBC 4.3.

|Nouvelle API|Description|Implémentation intéressante|  
|-----------------|-----------------|-------------------------------|  
|void java.sql.connection.beginRequest()|Indicateurs pour le pilote qu’une demande, une unité de travail, indépendante commence sur cette connexion. Pour plus d'informations, voir [java.sql.Connection](https://docs.oracle.com/javase/9/docs/api/java/sql/Connection.html#beginRequest--).|Enregistre les valeurs des champs de connexion qui sont modifiables par le biais des méthodes API publiques : `databaseAutoCommitMode`, `transactionIsolationLevel`, `networkTimeout`, `holdability`, `sendTimeAsDatetime`, `statementPoolingCacheSize`, `disableStatementPooling`, `serverPreparedStatementDiscardThreshold`, `enablePrepareOnFirstPreparedStatementCall `, `catalogName`, `sqlWarnings`, `useBulkCopyForBatchInsert `.|
|void java.sql.connection.endRequest()|Indicateurs pour le pilote d’une requête, une unité de travail, indépendante est terminée. Pour plus d'informations, voir [java.sql.Connection](https://docs.oracle.com/javase/9/docs/api/java/sql/Connection.html#endRequest--).|Ferme les instructions qui sont créées lors de l’unité de travail et restaure toutes les transactions ouvertes. La méthode rétablit également les modifications apportées aux champs de connexion qui sont répertoriés ci-dessus.|
