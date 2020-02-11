---
title: Mettre à niveau des bases de données répliquées | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- merge replication database upgrades [SQL Server replication]
- replication [SQL Server], upgrading
- transactional replication, upgrading databases
- snapshot replication [SQL Server], upgrading databases
- upgrading replicated databases
ms.assetid: 9926a4f7-bcd8-4b9b-9dcf-5426a5857116
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a356a6bad7b0756f148b43ed0cbf35e8d2ce9cc9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62775316"
---
# <a name="upgrade-replicated-databases"></a>Mettre à niveau des bases de données répliquées
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] prend en charge la mise à niveau des bases de données répliquées à partir des versions précédentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ; il n'est pas nécessaire d'interrompre l'activité des autres nœuds lorsqu'un nœud est en cours de mise à niveau. Prenez soin de respecter les règles relatives aux versions qui sont prises en charge dans une topologie :  
  
-   Toute version convient pour le serveur de distribution dès lors qu'elle est égale ou supérieure à celle du serveur de publication (en général, l'instance du serveur de distribution est la même que celle du serveur de publication).  
  
-   Toute version convient pour le serveur de publication dès lors qu'elle est inférieure ou égale à celle du serveur de distribution.  
  
-   La version de l'Abonné dépend du type de publication :  
  
    -   La version d'un Abonné à une publication transactionnelle peut être n'importe laquelle des deux versions du serveur de publication. Par exemple : un serveur de publication [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] en cours d'exécution peut avoir des Abonnés [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] et un serveur de publication [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] peut avoir des Abonnés [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)].  
  
    -   La version d'un Abonné à une publication de fusion peut être toute version inférieure ou égale à celle du serveur de publication.  
  
> [!NOTE]  
>  Cette rubrique est disponible dans la documentation d'aide du programme d'installation et dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Les liens vers des rubriques qui s'affichent en gras dans la documentation d'aide du programme d'installation font référence à des rubriques qui sont exclusivement disponibles dans la documentation en ligne.  
  
## <a name="run-the-log-reader-agent-for-transactional-replication-before-upgrade"></a>Exécuter l'Agent de lecture du journal pour la réplication transactionnelle avant la mise à niveau  
 Avant d'effectuer la mise à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], vous devez vous assurer que toutes les transactions validées de tables publiées ont été traitées par l'Agent de lecture du journal. Pour vous assurer que toutes les transactions ont été traitées, effectuez les étapes suivantes pour chaque base de données qui contient des publications transactionnelles :  
  
1.  Assurez-vous que l'Agent de lecture du journal s'exécute pour la base de données. Par défaut, cet agent s'exécute en permanence.  
  
2.  Arrêtez l'activité des utilisateurs sur les tables publiées.  
  
3.  Laissez à l'Agent de lecture du journal le temps de copier des transactions vers la base de données de distribution, puis arrêtez-le.  
  
4.  Exécutez [sp_replcmds](/sql/relational-databases/system-stored-procedures/sp-replcmds-transact-sql) pour vérifier que toutes les transactions ont été traitées. Le jeu de résultats de cette procédure doit être vide.  
  
5.  Exécutez [sp_replflush](/sql/relational-databases/system-stored-procedures/sp-replflush-transact-sql) pour fermer la connexion à partir de sp_replcmds.  
  
6.  Effectuez la mise à niveau de serveur vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
7.  Redémarrez l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et l'Agent de lecture du journal s'ils ne démarrent pas automatiquement après la mise à niveau.  
  
## <a name="run-agents-for-merge-replication-after-upgrade"></a>Exécution des agents de réplication de fusion après la mise à niveau  
 Après la mise à niveau, exécutez l'Agent d'instantané pour chaque publication de fusion et l'Agent de fusion pour chaque abonnement afin de mettre à jour les métadonnées de réplication. Vous n'avez pas à appliquer le nouvel instantané, car il n'est pas nécessaire pour réinitialiser les abonnements. Les métadonnées d'abonnement sont mises à jour lors de la première exécution de l'Agent de fusion après la mise à niveau. Ceci signifie que la base de données d'abonnement peut rester en ligne et active durant la mise à niveau du serveur de publication.  
  
 La réplication de fusion stocke les métadonnées de publication et d'abonnement dans un certain nombre de tables système des bases de données de publication et d'abonnement. L'Agent d'instantané met à jour les métadonnées de publication et l'Agent de fusion met à jour les métadonnées d'abonnement. Il faut uniquement générer un instantané de publication. Si une publication de fusion utilise des filtres paramétrés, chaque partition a également un instantané. Il n'est pas nécessaire de mettre à jour ces instantanés partitionnés.  
  
 Exécutez les agents à partir de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], du moniteur de réplication ou de la ligne de commande. Pour plus d'informations sur l'exécution de l'Agent d'instantané, consultez les rubriques suivantes :  
  
-   [Créer et appliquer l’instantané initial](../../../2014/relational-databases/replication/create-and-apply-the-initial-snapshot.md)  
  
-   [Démarrer et arrêter un Agent de réplication &#40;SQL Server Management Studio&#41;](../../relational-databases/replication/agents/start-and-stop-a-replication-agent-sql-server-management-studio.md)  
  
-   [Créer et appliquer l’instantané initial](../../../2014/relational-databases/replication/create-and-apply-the-initial-snapshot.md)  
  
-   [Concepts des exécutables de l'agent de réplication](../../../2014/relational-databases/replication/concepts/replication-agent-executables-concepts.md)  
  
 Pour plus d'informations sur l'exécution de l'Agent de fusion, consultez les rubriques suivantes :  
  
-   [Synchroniser un abonnement par extraction](../../../2014/relational-databases/replication/synchronize-a-pull-subscription.md)  
  
-   [Synchroniser un abonnement par envoi de notification](../../../2014/relational-databases/replication/synchronize-a-push-subscription.md)  
  
 Après avoir mis à niveau [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans une topologie qui utilise la réplication de fusion, modifiez le niveau de compatibilité de toutes les publications si vous voulez utiliser les nouvelles fonctionnalités.  
  
## <a name="upgrading-to-standard-workgroup-or-express-editions"></a>Mise à niveau vers les éditions Standard, Workgroup ou Express  
 Avant la mise à niveau d’une édition de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] vers une autre, vérifiez que les fonctionnalités que vous utilisez actuellement sont prises en charge dans l’édition vers laquelle vous mettez à niveau. Pour plus d’informations, consultez la section sur la réplication dans [fonctionnalités prises en charge par les éditions de SQL Server 2014](../../../2014/getting-started/features-supported-by-the-editions-of-sql-server-2014.md).  
  
## <a name="web-synchronization-for-merge-replication"></a>Synchronisation Web pour la réplication de fusion  
 L'option de synchronisation Web pour la réplication de fusion requiert la copie de l'Écouteur de réplication [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (replisapi.dll) dans le répertoire virtuel sur le serveur IIS (Internet Information Services) utilisé pour la synchronisation. Lorsque vous configurez la synchronisation Web, le fichier est copié dans le répertoire virtuel par l'Assistant Configuration de la synchronisation Web. Si vous mettez à niveau les composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installés sur le serveur IIS, vous devez manuellement copier replisapi.dll depuis le répertoire COM vers le répertoire virtuel sur le serveur IIS. Pour plus d’informations sur la synchronisation web, consultez [Configuration de la synchronisation web](../../../2014/relational-databases/replication/configure-web-synchronization.md).  
  
## <a name="restoring-a-replicated-database-from-an-earlier-version"></a>Restauration d'une base de données répliquée à partir d'une version antérieure  
 Pour vous assurer que les paramètres de réplication sont conservés lorsque vous restaurez la sauvegarde d'une base de données répliquée à partir d'une version précédente : effectuez la restauration vers un serveur et une base de données du même nom que le serveur et la base de données à l'origine de la sauvegarde.  
  
## <a name="see-also"></a>Voir aussi  
 [FAQ sur l’administration de la réplication](../../relational-databases/replication/administration/frequently-asked-questions-for-replication-administrators.md)   
 [Compatibilité descendante de la réplication](../../../2014/relational-databases/replication/replication-backward-compatibility.md)   
 [Mises à niveau de la version et de l'édition prises en charge](../../database-engine/install-windows/supported-version-and-edition-upgrades.md)   
 [Mettre à niveau vers SQL Server 2014](upgrade-sql-server.md)  
  
  
