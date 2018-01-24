---
title: "Planifier et tester le plan de mise à niveau du moteur de base de données | Microsoft Docs"
ms.custom: 
ms.date: 07/20/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: install-windows
ms.reviewer: 
ms.suite: sql
ms.technology: server-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19c5b725-7400-4881-af8f-fd232ca28234
caps.latest.revision: "16"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: fd45301f5ce4497a672ffd4a684f972b08ac8013
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/18/2018
---
# <a name="plan-and-test-the-database-engine-upgrade-plan"></a>Planifier et tester le plan de mise à niveau du moteur de base de données
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] Pour effectuer une mise à niveau réussie de [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)], quelle que soit l’approche, une planification appropriée est nécessaire.  
  
## <a name="release-notes-and-known-upgrade-issues"></a>Notes de publication et problèmes de mise à niveau connus  
 Avant d'effectuer la mise à niveau du [!INCLUDE[ssDE](../../includes/ssde-md.md)], consultez :

- [Notes de publication de SQL Server 2017](../../sql-server/sql-server-2017-release-notes.md) 
- [Notes de publication de SQL Server 2016](../../sql-server/sql-server-2016-release-notes.md) 
- [Compatibilité descendante du moteur de base de données SQL Server](../../database-engine/sql-server-database-engine-backward-compatibility.md).  
  
## <a name="pre-upgrade-planning-checklist"></a>Liste de vérification pour la planification d’une mise à niveau  
 Avant la mise à niveau du [!INCLUDE[ssDE](../../includes/ssde-md.md)], consultez la liste de vérification suivante et les rubriques associées. Ces rubriques s’appliquent à toutes les mises à jour, quelle que soit la méthode utilisée, et vous aide à déterminer la méthode de mise à niveau la plus appropriée : mise à niveau propagée, mise à niveau de nouvelle installation ou mise à niveau sur place. Par exemple, il se peut que vous ne soyez pas en mesure d’effectuer une mise à niveau sur place ou une mise à niveau propagée si vous mettez à niveau le système d’exploitation, mettez à niveau à partir de SQL Server 2005 ou mettez à niveau à partir d’une version 32 bits de SQL Server. Pour un arbre de décision, voir [Choose a Database Engine Upgrade Method](../../database-engine/install-windows/choose-a-database-engine-upgrade-method.md).  
  
-   **Configurations matérielle et logicielle requises :** consultez les configurations matérielle et logicielle requises pour l’installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Vous pouvez les trouver dans l’article suivant : [Configuration matérielle et logicielle requises pour l’installation de SQL Server](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md). Une partie du cycle de planification de toute mise à niveau consiste à prendre en compte la mise à niveau matérielle (un matériel plus récent est plus rapide et peut réduire le travail de gestion des licences, en raison soit du moindre nombre de processeurs, soit de la consolidation de la base de données et du serveur) et la mise à niveau du système d’exploitation. Ces modifications matérielles et logicielles affectent le choix de la méthode de mise à niveau.  
  
-   **Environnement actuel :** examinez votre environnement actuel pour déterminer les composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilisés et les clients qui se connectent à votre environnement.  
  
    -   **Fournisseurs de client :** bien que la mise à niveau ne nécessite pas de mise à jour du fournisseur pour chacun de vos clients, vous pouvez choisir de la faire. Si vous effectuez la mise à niveau de [!INCLUDE[sql14](../../includes/sssql14-md.md)] ou version antérieure, les fonctionnalités [!INCLUDE[sql15](../../includes/sssql15-md.md)] suivantes peuvent nécessiter un fournisseur mis à jour pour chaque client ou qu’un fournisseur mis à jour fournisse des fonctionnalités supplémentaires :  
  
       -   [Always Encrypted &#40;moteur de base de données&#41;](../../relational-databases/security/encryption/always-encrypted-database-engine.md)  
  
       -   [Stretch Database](../../sql-server/stretch-database/stretch-database.md)  
  
       -   [Écouteurs de groupe de disponibilité, connectivité client et basculement d’application &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/listeners-client-connectivity-application-failover.md)  
  
       -   Mise à jour de sécurité SSL  

   >[!NOTE]
   >La liste précédente s’applique également à [!INCLUDE[sscurrent](../../includes/sscurrent-md.md)].
  
-   **Composants tiers :** déterminez la compatibilité des composants tiers, telle la sauvegarde intégrée.  
  
-   **Environnement cible :** vérifiez que votre environnement cible présente les configurations matérielle et logicielle requise, et peut prendre en charge le système d’origine. Par exemple, la mise à niveau peut impliquer la consolidation de plusieurs instances SQL Server en une seule instance [!INCLUDE[ssnoversion](../../includes/ssnoversion-md.md)] nouvelle, ou la virtualisation de votre environnement [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans un cloud privé ou public.  
  
-   **Édition :** déterminez l’édition appropriée de [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] pour votre mise à niveau, déterminez les chemins de mise à niveau appropriés. Pour plus d'informations, consultez [Supported Version and Edition Upgrades](../../database-engine/install-windows/supported-version-and-edition-upgrades.md). Avant toute mise à niveau d'une édition de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers une autre, vérifiez que la fonctionnalité en cours d'utilisation est prise en charge dans l'édition vers laquelle vous effectuez la mise à niveau.  
  
    > [!NOTE]  
    >  Quand vous mettez à niveau [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] à partir d’une version antérieure de l'édition Enterprise de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], choisissez Enterprise Edition : contrat de licence selon le nombre de cœurs ou Enterprise Edition. Ces éditions Enterprise se différencient uniquement par leur mode de licences. Pour plus d’informations, voir [Compute Capacity Limits by Edition of SQL Server](../../sql-server/compute-capacity-limits-by-edition-of-sql-server.md).  
  
-   **Compatibilité descendante :** consultez la rubrique relative à la compatibilité descendante du moteur de base de données [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] pour connaître les changements de comportement entre [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] et la version de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] que vous mettez à niveau. Consultez [SQL Server Database Engine Backward Compatibility](../../database-engine/sql-server-database-engine-backward-compatibility.md).  
  
-   **Conseiller de mise à niveau :**  exécutez le Conseiller de mise à niveau [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] afin de diagnostiquer d’éventuels problèmes susceptibles de bloquer le processus de mise à niveau ou de nécessiter une modification d’applications ou de scripts existants en raison d’une modification avec rupture. [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] contient une nouvelle version du Conseiller de mise à niveau pour aider les clients à préparer la mise à niveau d’un système existant.  Cet outil offre également la possibilité de vérifier vos bases de données existantes pour voir si elles peuvent tirer parti de nouvelles fonctionnalités, telles que les tables d’extension, après la mise à niveau.   
    Vous pouvez télécharger le [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)]Conseiller de mise à niveau  [ici](https://www.microsoft.com/en-us/download/details.aspx?id=48119).  
  
-   **Outil d’analyse de configuration système :**  exécutez l’Outil d’analyse de configuration système (SCC) [!INCLUDE[ssCurrent](../../includes/ssnoversion-md.md)] pour déterminer si le programme d’installation de SQL Server détecte des problèmes majeurs avant de planifier réellement la mise à niveau. Pour plus d'informations, consultez [Check Parameters for the System Configuration Checker](../../database-engine/install-windows/check-parameters-for-the-system-configuration-checker.md).  
  
-   **Mise à niveau des tables optimisées en mémoire :** lors de la mise à niveau d’une instance de base de données SQL Server 2014 contenant des tables optimisées en mémoire pour SQL Server 2016, le processus nécessite plus de temps pour convertir les tables optimisées en mémoire vers le nouveau format sur disque. Par ailleurs, la base de données est hors connexion pendant ces étapes.   Le temps nécessaire dépend de la taille des tables mémoire optimisées et de la vitesse du sous-système d’E/S. La mise à niveau nécessite trois tailles d’opérations de données pour les mises à niveau sur place et de nouvelle installation (pour une mise à niveau propagée, l’étape 1 n’est pas requise, mais les étapes 2 et 3 le sont) :  
  
    1.  Exécutez la récupération de base de données à l’aide de l’ancien format sur disque (cela inclut le chargement de toutes les données dans des tables mémoire optimisées en mémoire à partir du disque).  
  
    2.  Sérialisez les données sur le disque dans le nouveau format sur disque.  
  
    3.  Exécutez la récupération de base de données en utilisant le nouveau format (cela inclut le chargement de toutes les données dans des tables mémoire optimisées en mémoire à partir du disque).  
  
     En outre, un manque d’espace sur le disque pendant l’exécution de ce processus entraîne un échec de restauration. Assurez-vous que l’espace est suffisant sur le disque pour stocker la base de données existante plus le stockage supplémentaire égal à la taille actuelle des conteneurs du groupe de fichiers MEMORY_OPTIMIZED_DATA dans la base de données pour effectuer une mise à niveau sur place, ou attacher une base de données SQL Server 2014 à une instance SQL Server 2016. Utilisez la requête suivante pour déterminer l’espace disque actuellement requis pour le groupe de fichiers MEMORY_OPTIMIZED_DATA, et donc également l’espace disque disponible requis pour que la mise à niveau réussisse :  
  
    ```  
    select cast(sum(size) as float)*8/1024/1024 'size in GB'   
    from sys.database_files  
    where data_space_id in (select data_space_id from sys.filegroups where type=N'FX')  
    ```  
  
## <a name="develop-and-test-the-upgrade-plan"></a>Développer et tester le plan de mise à niveau  
 La meilleure approche consiste à traiter la mise à niveau comme tout projet informatique. Vous devez mettre en place une équipe de mise à niveau disposant des compétences requises en matière d’administration de base de données, de réseau, d’extraction, de transformation, de chargement et autres. L’équipe doit :  
  
-   **Choisir la méthode de mise à niveau :** consultez [Choisissez une méthode de mise à niveau du moteur de base de données](../../database-engine/install-windows/choose-a-database-engine-upgrade-method.md).  
  
-   **Développer un plan de restauration :** L’exécution de ce plan vous permettra de restaurer votre environnement d’origine en cas de nécessité.  
  
-   **Déterminer les critères d’acceptation :** vous devez savoir si la mise à niveau a réussi avant de faire passer les utilisateurs à l’environnement mis à niveau.  
  
-   **Tester le plan de mise à niveau :** pour tester les performances à l’aide de votre charge de travail réelle, servez-vous de l’utilitaire Microsoft SQL Server Distributed Replay. Celui-ci peut utiliser plusieurs ordinateurs pour relire les données de trace, en simulant une charge de travail stratégique. En effectuant une nouvelle lecture sur un serveur de test avant et après une mise à niveau de SQL Server, vous pouvez mesurer les écarts de performances et rechercher toute incompatibilité entre votre application et la mise à niveau. Pour plus d’informations, consultez [SQL Server Distributed Replay](../../tools/distributed-replay/sql-server-distributed-replay.md) et [Options de ligne de commande de l’outil d’administration &#40;Distributed Replay Utility&#41;](../../tools/distributed-replay/administration-tool-command-line-options-distributed-replay-utility.md).  
  
## <a name="next-steps"></a>Étapes suivantes  
 [Mettre à niveau le moteur de base de données](../../database-engine/install-windows/upgrade-database-engine.md)  
  
  
