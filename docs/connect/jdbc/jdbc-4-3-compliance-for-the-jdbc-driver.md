---
description: Compatibilité avec JDBC 4.3 pour le pilote JDBC
title: Conformité JDBC 4.3 pour le pilote | Microsoft Docs
ms.custom: ''
ms.date: 08/12/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 36025ec0-3c72-4e68-8083-58b38e42d03b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e4ce01ec71649549166aa6a3d2f33d9dbb157e08
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88438351"
---
# <a name="jdbc-43-compliance-for-the-jdbc-driver"></a>Compatibilité avec JDBC 4.3 pour le pilote JDBC

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

> [!NOTE]  
> Les versions antérieures à Microsoft JDBC Driver 6.4 pour SQL Server sont conformes uniquement aux spécifications de l’API Java Database Connectivity (JDBC) 4.2. Cette section ne s’applique pas aux versions qui contiennent la version 6.4 et antérieures à celle-ci.

Depuis la version 6.4, Microsoft JDBC Driver pour SQL Server est compatible avec JAVA 9 et lève `SQLFeatureNotSupportedException` pour les nouvelles API JDBC 4.3 qui contiennent des méthodes non implémentées.

Avec la version Microsoft JDBC Driver 7.0 pour SQL Server, le pilote est désormais compatible avec JAVA 10 et prend en charge les API mentionnées ci-dessous. Le pilote lève `SQLFeatureNotSupportedException` pour les autres méthodes non implémentées à partir des spécifications JDBC 4.3.

|Nouvelle API|Description|Implémentation intéressante|  
|-----------------|-----------------|-------------------------------|  
|void java.sql.connection.beginRequest()|Informations indiquant au pilote qu’une requête, une unité de travail indépendante, commence sur cette connexion. Pour plus d'informations, voir [java.sql.Connection](https://docs.oracle.com/javase/9/docs/api/java/sql/Connection.html#beginRequest--).|Enregistre les valeurs des champs de connexion qui peuvent être modifiés par le biais de méthodes API publiques : `databaseAutoCommitMode`, `transactionIsolationLevel`, `networkTimeout`, `holdability`, `sendTimeAsDatetime`, `statementPoolingCacheSize`, `disableStatementPooling`, `serverPreparedStatementDiscardThreshold`, `enablePrepareOnFirstPreparedStatementCall`, `catalogName`, `sqlWarnings`, `useBulkCopyForBatchInsert`.|
|void java.sql.connection.endRequest()|Informations indiquant au pilote qu’une requête, une unité de travail indépendante, est terminée. Pour plus d'informations, voir [java.sql.Connection](https://docs.oracle.com/javase/9/docs/api/java/sql/Connection.html#endRequest--).|Ferme les instructions créées pendant l’unité de travail et restaure toutes les transactions ouvertes. La méthode rétablit également les modifications apportées aux champs de connexion répertoriés ci-dessus.|
