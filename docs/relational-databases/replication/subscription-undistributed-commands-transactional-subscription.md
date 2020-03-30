---
title: Commandes non distribuées (moniteur de réplication)
description: Décrit l’onglet « Commandes non distribuées » du moniteur de réplication dans SQL Server Management Studio (SSMS).
ms.custom: seo-lt-2019
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.monitor.subscription.performance.f1
ms.assetid: 5451561e-0ce3-4bb5-844a-88cd15b0b371
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-current||>=sql-server-2014||=sqlallproducts-allversions
ms.openlocfilehash: 09271bf91d561e86fdf6525ccd217bb000449044
ms.sourcegitcommit: 58158eda0aa0d7f87f9d958ae349a14c0ba8a209
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/30/2020
ms.locfileid: "75321395"
---
# <a name="subscription-undistributed-commands-transactional-subscription"></a>Abonnement, commandes non distribuées (abonnement transactionnel)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md.md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  L'onglet **Commandes non distribuées** contient des informations sur le nombre de commandes de la base de données de distribution qui n'ont pas été distribuées à l'abonné sélectionné, ainsi que le délai estimé de distribution de ces commandes. Pour plus d’informations sur l’affichage des commandes dans la base de données de distribution, consultez [sp_replshowcmds &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-replshowcmds-transact-sql.md).  

[!INCLUDE[azure-sql-db-replication-supportability-note](../../includes/azure-sql-db-replication-supportability-note.md)]
  
## <a name="options"></a>Options  
 **Nombre de commandes dans la base de données de distribution attendant d'être appliquées à cet abonné.**  
 Nombre de commandes dans la base de données de distribution qui n'ont pas été distribuées à l'abonné sélectionné. Une commande est constituée d'une instruction DML (Data Manipulation Language) Transact-SQL ou d'une instruction DDL (Data Definition Language).  
  
 **Temps estimé pour appliquer ces commandes, sur base des performances passées**  
 Délai estimé de distribution des commandes à l'Abonné. Si cette valeur est supérieure au délai nécessaire pour générer et appliquer un instantané à l'Abonné, réinitialisez l'Abonné. Pour plus d’informations, consultez [Réinitialiser des abonnements](../../relational-databases/replication/reinitialize-subscriptions.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Démarrer le Moniteur de réplication](../../relational-databases/replication/monitor/start-the-replication-monitor.md)   
 [Analyser les performances avec le moniteur de réplication](../../relational-databases/replication/monitor/monitor-performance-with-replication-monitor.md)   
 [Surveillance de la réplication](../../relational-databases/replication/monitor/monitoring-replication.md)  
  
  
