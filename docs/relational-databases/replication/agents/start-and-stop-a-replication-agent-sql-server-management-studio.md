---
title: Démarrer et arrêter un Agent de réplication (SSMS)
description: Découvrez comment démarrer et arrêter un Agent de réplication dans SQL Server Management Studio et le moniteur de réplication.
ms.custom: seo-lt-2019
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- agents [SQL Server replication], stopping
- agents [SQL Server replication], starting
ms.assetid: 97977c4a-8c7c-4a22-9480-69aa812bd1e5
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016
ms.openlocfilehash: 1cddb10655acce42c621a8032edd5e75226c1c5e
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97467310"
---
# <a name="start-and-stop-a-replication-agent-sql-server-management-studio"></a>Démarrer et arrêter un Agent de réplication (SQL Server Management Studio)
[!INCLUDE[sql-asdbmi](../../../includes/applies-to-version/sql-asdbmi.md)]
  Démarrez et arrêtez des agents à partir du dossier **Travaux** et du dossier **Réplication** de [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou à partir du moniteur de réplication. Démarrez et arrêtez les Agents et les travaux suivants :  
  
-   Agent d'instantané, utilisé par toutes les publications  
  
-   Agent de lecture du journal, utilisé par toutes les publications transactionnelles  
  
-   Agent de lecture de la file d'attente, utilisé par les publications transactionnelles qui possèdent des abonnements mis à jour en attente  
  
-   Agent de distribution, qui synchronise les abonnements aux publications transactionnelles et d'instantané  
  
-   Agent de fusion, qui synchronise les abonnements aux publications de fusion  
  
-   Travaux de maintenance de la réplication  
  
 Pour plus d’informations sur le démarrage de l’Agent de fusion et de l’Agent de Distribution, consultez [Synchroniser un abonnement par émission de données](../../../relational-databases/replication/synchronize-a-push-subscription.md) et [Synchroniser un abonnement par extraction](../../../relational-databases/replication/synchronize-a-pull-subscription.md). Pour plus d’informations sur les travaux de maintenance, consultez [Exécuter des travaux de maintenance de réplication &#40;SQL Server Management Studio&#41;](../../../relational-databases/replication/administration/run-replication-maintenance-jobs-sql-server-management-studio.md).  
  
 Pour plus d’informations sur le démarrage du Moniteur de réplication, consultez [Démarrer le Moniteur de réplication](../../../relational-databases/replication/monitor/start-the-replication-monitor.md).  
  
### <a name="to-start-and-stop-a-snapshot-agent-or-log-reader-agent-from-management-studio"></a>Pour démarrer et arrêter un Agent d'instantané ou un Agent de lecture du journal à partir de Management Studio  
  
1.  Connectez-vous au serveur de publication dans [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]puis développez le nœud du serveur et le dossier **Réplication** .  
  
2.  Développez le dossier **Publications locales** , puis cliquez avec le bouton droit sur une publication.  
  
3.  Cliquez sur **Afficher l'état de l'Agent d'instantané** ou **Afficher l'état de l'Agent de lecture du journal**.  
  
4.  Cliquez sur **Démarrer** ou sur **Arrêter**.  
  
### <a name="to-start-and-stop-a-queue-reader-agent-from-management-studio"></a>Pour démarrer et arrêter un Agent de lecture de file d'attente à partir de Management Studio  
  
1.  Connectez-vous au serveur de distribution dans [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le dossier **Agent SQL Server** puis développez le dossier **Travaux** .  
  
3.  Cliquez avec le bouton droit sur le travail de l'agent puis cliquez sur **Démarrer le travail** ou **Arrêter le travail**. Le nom du travail de l’Agent de lecture de la file d’attente est au format **[\<Distributor>].\<integer>** .  
  
### <a name="to-start-and-stop-a-snapshot-agent-log-reader-agent-or-queue-reader-agent-from-replication-monitor"></a>Pour démarrer et arrêter un Agent d'instantané, un Agent de lecture du journal ou un Agent de lecture de file d'attente dans le moniteur de réplication  
  
1.  Développez un groupe de serveurs de publication dans le volet gauche, développez un serveur de publication, puis cliquez sur une publication.  
  
2.  Cliquez sur l'onglet **Agents** .  
  
3.  Cliquez avec le bouton droit sur un Agent puis cliquez sur **Démarrer l'Agent** ou **Arrêter l'Agent**.  
  
## <a name="see-also"></a>Voir aussi  
 [Surveillance de la réplication](../../../relational-databases/replication/monitor/monitoring-replication.md)   
 [Concepts des exécutables de l’Agent de réplication](../../../relational-databases/replication/concepts/replication-agent-executables-concepts.md)   
 [Présentation des Agents de réplication](../../../relational-databases/replication/agents/replication-agents-overview.md)  
  
  
