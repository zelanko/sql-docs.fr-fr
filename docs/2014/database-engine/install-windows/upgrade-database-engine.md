---
title: Mettre à niveau le moteur de base de données | Microsoft Docs
ms.custom: ''
ms.date: 10/26/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- compatibility [SQL Server], databases
- compatibility levels [SQL Server], after upgrade
- Database Engine [SQL Server], upgrading
ms.assetid: 3c036813-36cf-4415-a0c9-248d0a433859
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ed13712678ab599e55b539d6226142b686106fe5
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84931955"
---
# <a name="upgrade-database-engine"></a>Mettre à niveau le moteur de base de données
  Cette rubrique fournit les informations qui vous aideront à préparer et à comprendre le processus de mise à niveau :  
  
-   Problèmes de mise à niveau connus  
  
-   Tâches précédant la mise à niveau et observations  
  
-   Liens vers les rubriques consacrées aux procédures de mise à niveau du [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
-   Liens vers les rubriques consacrées aux procédures de migration des bases de données vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]  
  
-   Remarques sur les clusters de basculement  
  
-   Tâches postérieures à la mise à niveau et observations  
  
## <a name="known-upgrade-issues"></a>Problèmes de mise à niveau connus  
 Avant d'effectuer la mise à niveau du [!INCLUDE[ssDE](../../includes/ssde-md.md)], consultez [SQL Server Database Engine Backward Compatibility](../sql-server-database-engine-backward-compatibility.md). Pour plus d’informations sur les scénarios de mise à niveau pris en charge et les problèmes de mise à niveau connus, consultez [Mises à niveau de la version et de l’édition prises en charge](supported-version-and-edition-upgrades.md). Pour plus d'informations sur la compatibilité descendante des autres composants de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , consultez [Backward Compatibility](../../getting-started/backward-compatibility.md).  
  
> [!IMPORTANT]  
>  Avant toute mise à niveau d'une édition de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers une autre, vérifiez que la fonctionnalité en cours d'utilisation est prise en charge dans l'édition vers laquelle vous effectuez la mise à niveau.  
  
> [!NOTE]  
>  Lorsque vous effectuez la mise à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] d'une version antérieure de l'édition Enterprise de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , choisissez entre Enterprise Edition : contrat de licence selon le nombre de cœurs et Enterprise Edition. Ces éditions Enterprise se différencient uniquement par leur mode de licences. Pour plus d’informations, voir [Compute Capacity Limits by Edition of SQL Server](../../sql-server/compute-capacity-limits-by-edition-of-sql-server.md).  
  
## <a name="pre-upgrade-checklist"></a>Liste de contrôle préalable à la mise à niveau  
 La mise à niveau vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à partir d'une version précédente est prise en charge par le programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Vous pouvez également migrer les bases de données à partir de versions précédentes de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . La migration peut être effectuée à partir d'une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers une autre instance située vers le même ordinateur ou à partir d'une instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers un autre ordinateur. Les options de migration incluent l'utilisation de l'Assistant Copie de base de données, de la fonctionnalité de sauvegarde et de restauration, ainsi que l'utilisation de l'Assistant Importation et exportation [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] et des méthodes d'importation et d'exportation en bloc.  
  
 Avant de mettre à niveau le [!INCLUDE[ssDE](../../includes/ssde-md.md)], consultez les rubriques suivantes :  
  
-   Consultez [Hardware and Software Requirements for Installing SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).  
  
-   Consultez [Check Parameters for the System Configuration Checker](check-parameters-for-the-system-configuration-checker.md).  
  
-   Consultez [Security Considerations for a SQL Server Installation](../../sql-server/install/security-considerations-for-a-sql-server-installation.md).  
  
-   Consultez [Mises à niveau de la version et de l’édition prises en charge](supported-version-and-edition-upgrades.md).  
  
-   Consultez [Utiliser le Conseiller de mise à niveau pour la préparation des mises à niveau](../../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md).  
  
-   Consultez [Utiliser Distributed Replay Utility pour préparer des mises à niveau](../../sql-server/install/use-the-distributed-replay-utility-to-prepare-for-upgrades.md).  
  
-   Consultez [SQL Server Database Engine Backward Compatibility](../sql-server-database-engine-backward-compatibility.md).  
  
-   Consultez [Migrer des plans de requête](change-the-database-compatibility-mode-and-use-the-query-store.md).  
  
 Passez en revue les problèmes ci-dessous et apportez les modifications nécessaires, avant d'effectuer la mise à niveau de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:  
  
-   Lors de la mise à niveau des instances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] où l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est inscrit dans les relations MSX/TSX, mettez à niveau les serveurs cibles avant de mettre à niveau les serveurs maîtres. Si vous mettez à niveau les serveurs maîtres avant les serveurs cibles, l'Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne sera pas en mesure de se connecter aux instances principales de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   Lorsque vous procédez à une mise à niveau à partir d'une version 64 bits de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] vers une version 64 bits de [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], vous devez mettre à niveau [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] avant de mettre à niveau le [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
-   Sauvegardez tous les fichiers de base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] de l'instance à mettre à niveau, afin de pouvoir les restaurer, si besoin est.  
  
-   Exécutez les commandes DBCC (Database Console Commands) appropriées sur les bases de données à mettre à niveau afin de vérifier leur cohérence.  
  
-   Estimez l'espace disque requis pour mettre à niveau les composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , ainsi que les bases de données utilisateur. Pour connaître l'espace disque requis par les composants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , consultez [Hardware and Software Requirements for Installing SQL Server 2014](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md).  
  
-   Vérifiez que les bases de données système de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] - master, model, msdb et tempdb - sont configurées pour s'accroître automatiquement et vérifiez qu'elles disposent pour cela d'un espace disque suffisant.  
  
-   Vérifiez que tous les serveurs de bases de données possèdent des informations d'ouverture de session dans la base de données master. Ce point est particulièrement important pour la restauration d'une base de données, car les informations d'ouverture de session système résident dans la base de données master.  
  
-   Désactivez toutes les procédures stockées de démarrage, car le processus de mise à niveau arrête et démarre les services sur l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] en cours de mise à niveau. Les procédures stockées traitées au moment du démarrage pourraient bloquer le processus de mise à niveau.  
  
-   Assurez-vous que la réplication est activé et arrêtez la réplication.  
  
-   Quittez toutes les applications, y compris tous les services ayant des dépendances de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . La mise à niveau peut échouer si les applications locales sont connectées à l'instance en cours de mise à niveau.  
  
-   Pour plus d’informations, consultez [Réduire le temps d’indisponibilité des bases de données mises en miroir lors de la mise à niveau d’instances de serveur](../database-mirroring/upgrading-mirrored-instances.md).  
  
## <a name="upgrading-the-database-engine"></a>Mise à niveau du moteur de base de données  
 Vous pouvez remplacer une installation de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou ultérieur par une mise à niveau de la version. Si une version précédente de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est détectée lorsque vous exécutez le programme d'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , tous les fichiers programme de la version précédente de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] sont mis à niveau et toutes les données stockées dans l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] précédente sont conservées. En outre, les versions précédentes de la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] demeureront intactes sur l'ordinateur.  
  
> [!WARNING]  
>  Quand vous exécutez le programme d’installation de SQL Server 2014, l’instance SQL Server est arrêtée, puis redémarrée dans le cadre de l’exécution des vérifications préalables à la mise à niveau.  
  
> [!CAUTION]  
>  Lorsque vous effectuerez une mise à niveau vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] précédente sera remplacée et n'existera plus sur votre ordinateur. Avant d'opérer la mise à niveau, sauvegardez les bases de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et les autres objets associés à l'instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] précédente.  
  
 Vous pouvez mettre à niveau le [!INCLUDE[ssDE](../../includes/ssde-md.md)] en utilisant l'Assistant Installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
### <a name="database-compatibility-level-after-upgrade"></a>Niveau de compatibilité des bases de données après une mise à niveau  
 Les niveaux de compatibilité des `tempdb` `model` `msdb` bases de données de **ressources** , et sont définis sur 120 après la mise à niveau. La base de données système `master` conserve le niveau de compatibilité qu'elle avait avant la mise à niveau.  
  
 Si le niveau de compatibilité d'une base de données utilisateur est à 100 ou supérieur avant la mise à niveau, il reste le même après la mise à niveau. Si le niveau de compatibilité était à 90 avant la mise à niveau, dans la base de données mise à niveau, le niveau de compatibilité est défini à 100, ce qui correspond au niveau de compatibilité le plus bas pris en charge dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
> [!NOTE]  
>  Les nouvelles bases de données utilisateur héritent du niveau de compatibilité de la base de données `model`.  
  
## <a name="migrating-databases"></a>Migration des bases de données  
 Vous pouvez déplacer les bases de données utilisateur vers une instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] à l'aide des fonctionnalités de sauvegarde et de restauration ou de détachement et d'attachement de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [Copier des bases de données avec la sauvegarde et la restauration](../../relational-databases/databases/copy-databases-with-backup-and-restore.md) ou [Attacher et détacher une base de données &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md).  
  
> [!IMPORTANT]  
>  Une base de données dont le nom est identique sur les serveurs source et de destination ne peut pas être déplacée ni copiée. Dans ce cas, elle est signalée par « Existe déjà ».  
  
 Pour plus d'informations, consultez [Use the Copy Database Wizard](../../relational-databases/databases/use-the-copy-database-wizard.md).  
  
## <a name="after-upgrading-the-database-engine"></a>Après la mise à niveau du moteur de base de données  
 Après la mise à niveau du [!INCLUDE[ssDE](../../includes/ssde-md.md)], effectuez les tâches suivantes :  
  
-   Réinscrivez vos serveurs. Pour plus d’informations sur l’inscription des serveurs, consultez [Inscrire des serveurs](../../ssms/register-servers/register-servers.md).  
  
-   Alimentez à nouveau les catalogues de texte intégral pour garantir la cohérence sémantique dans les résultats de la requête.  
  
     [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] installe de nouveaux analyseurs lexicaux pour la recherche en texte intégral et sémantique. Les analyseurs lexicaux sont utilisés au moment de l'indexation et au moment de la requête. Si vous ne reconstruisez pas les catalogues de texte intégral, vos résultats de recherche peuvent être incohérents. Si vous exécutez une requête de texte intégral qui recherche une expression qui est divisée différemment par l'analyseur lexical dans une version précédente de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et l'analyseur lexical actuel, une ligne ou un document contenant l'expression peut ne pas être extrait. Cela est dû au fait que les expressions indexées ont été divisées à l'aide d'une logique différente de celle de la requête utilise. La solution consiste à réalimenter (reconstruire) les catalogues de texte intégral avec les nouveaux analyseurs lexicaux afin que le temps d'indexation et le comportement de cette requête soient identiques.  
  
     Pour plus d’informations, consultez [sp_fulltext_catalog &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-fulltext-catalog-transact-sql).  
  
-   Configurez l'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Pour réduire la surface d'exposition d'un système, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installe et active de façon sélective les services et fonctionnalités clés.  
  
-   Validez ou supprimez les indicateurs USE PLAN générés par [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et appliqués aux requêtes sur les tables partitionnées et les index.  
  
     [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] modifie la manière dont sont traitées les requêtes sur les tables partitionnées et les index. Les requêtes sur les objets partitionnés qui utilisent l'indicateur USE PLAN pour un plan généré par [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] peuvent contenir un plan non utilisable dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]. Nous recommandons les procédures suivantes après la mise à niveau vers [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].  
  
     **Lorsque l'indicateur USE PLAN conseil est spécifié directement dans une requête :**  
  
    1.  Supprimez l'indicateur USE PLAN de la requête.  
  
    2.  Testez la requête.  
  
    3.  Si l'optimiseur ne sélectionne pas un plan approprié, réglez la requête, puis envisagez de spécifier l'indicateur USE PLAN avec le plan de requête désiré.  
  
     **Lorsque l'indicateur USE PLAN conseil est spécifié dans un repère de plan :**  
  
    1.  Utilisez la fonction sys.fn_validate_plan_guide pour vérifier la validité du repère de plan. Vous pouvez aussi surveiller les repères de plan non valides en utilisant l'événement Plan Guide Unsuccessful dans [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].  
  
    2.  Si le repère de plan n'est pas valide, abandonnez-le. Si l'optimiseur ne sélectionne pas un plan approprié, réglez la requête, puis envisagez de spécifier l'indicateur USE PLAN avec le plan de requête désiré.  
  
     Un repère de plan non valide n'entraîne pas l'échec d'une requête quand l'indicateur USE PLAN est spécifié dans un repère de plan. À la place, la requête est compilée sans utiliser l'indicateur USE PLAN.  
  
 Toutes les bases de données qui étaient marquées comme activées ou désactivées pour le texte intégral avant la mise à niveau conservent ce statut après la mise à niveau. Après la mise à niveau, les catalogues de texte intégral sont automatiquement reconstruits et alimentés pour toutes les bases de données activées pour le texte intégral. Cette opération peut s'avérer gourmande en termes de temps et de ressources. Vous pouvez suspendre temporairement l'opération d'indexation de texte intégral en exécutant l'instruction suivante :  
  
```  
EXEC sp_fulltext_service 'pause_indexing', 1;  
```  
  
 Pour reprendre l'alimentation de l'index de recherche en texte intégral, exécutez l'instruction suivante :  
  
```  
EXEC sp_fulltext_service 'pause_indexing', 0;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Mises à niveau de la version et de l'édition prises en charge](supported-version-and-edition-upgrades.md)   
 [Utiliser plusieurs versions et instances de SQL Server](../../../2014/sql-server/install/work-with-multiple-versions-and-instances-of-sql-server.md)   
 [Compatibilité descendante](../../getting-started/backward-compatibility.md)   
 [Mettre à niveau des bases de données répliquées](upgrade-replicated-databases.md)  
  
  
