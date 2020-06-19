---
title: Améliorer les performances des index de recherche en texte intégral | Microsoft Docs
ms.custom: ''
ms.date: 04/26/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- performance [SQL Server], full-text search
- full-text queries [SQL Server], performance
- crawls [full-text search]
- full-text indexes [SQL Server], performance
- full-text search [SQL Server], performance
- batches [SQL Server], full-text search
ms.assetid: ef39ef1f-f0b7-4582-8e9c-31d4bd0ad35d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 51b5913e9c3ce65faa5a1fddc5846cc7c94d149f
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85063244"
---
# <a name="improve-the-performance-of-full-text-indexes"></a>Améliorer les performances des index de recherche en texte intégral
  Les performances de l'indexation de texte intégral et des requêtes de texte intégral sont influencées par les ressources matérielles telles que la mémoire, la vitesse du disque et de l'UC ainsi que l'architecture de l'ordinateur.  
  
##  <a name="common-causes-of-performance-issues"></a><a name="causes"></a>Causes courantes des problèmes de performances  
 La cause principale d'une baisse des performances de l'indexation de texte intégral est les limites liées aux ressources matérielles :  
  
-   Si l’utilisation de l’UC par le processus hôte de démon de filtre (fdhost.exe) ou le processus (sqlservr.exe) [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] approche des 100 pour cent, le processeur est le goulet d’étranglement.  
  
-   Si la longueur moyenne de la file d'attente du disque est plus de deux fois supérieure au nombre de têtes de disque, le disque est engorgé. La première solution consiste à créer des catalogues de texte intégral distincts des fichiers et des journaux de la base de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Placez les journaux, les fichiers de base de données et les catalogues de texte intégral sur des disques distincts. L'achat de disques plus rapides et l'utilisation de RAID peuvent également contribuer à l'amélioration des performances d'indexation.  
  
-   En cas de manque de mémoire physique (limite de 3 Go), la mémoire est engorgée. Les limitations de mémoire physique sont possibles sur tous les systèmes, et sur les systèmes 32 bits, la pression de mémoire virtuelle peut ralentir l'indexation de texte intégral.  
  
    > [!NOTE]  
    >  À partir de [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], le moteur d'indexation et de recherche en texte intégral peut utiliser la mémoire AWE parce que le moteur d'indexation et de recherche en texte intégral fait partie du sqlservr.exe.  
  
 Si le système ne rencontre aucun goulet d'étranglement matériel, les performances d'indexation de la recherche en texte intégral dépendent essentiellement des éléments suivants :  
  
-   Durée de création des traitements de texte intégral par [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   Rapidité d'utilisation de ces traitements par le démon de filtre.  
  
> [!NOTE]  
>  Contrairement à un remplissage complet, le remplissage du suivi des modifications automatique, incrémentiel ou manuel n'a pas pour objectif de maximiser les ressources matérielles en vue d'obtenir une vitesse supérieure. Par conséquent, ces suggestions de paramétrage peuvent ne pas améliorer les performances de l'indexation de texte intégral.  
  
 À la fin d'une alimentation, une fusion finale est déclenchée ; les fragments d'index sont fusionnés entre eux dans un index de recherche en texte intégral. Il en résulte une amélioration des performances des requêtes dans la mesure où seul l'index principal doit être interrogé au lieu des fragments d'index ; par ailleurs, les statistiques de score sont plus appropriées pour un classement en fonction de la pertinence. Notez que la fusion principale peut nécessiter de nombreuses entrées/sorties, car de grandes quantités de données doivent être écrites et lues lors de la fusion des fragments d'index. Toutefois, cela ne bloque pas les requêtes entrantes.  
  
> [!IMPORTANT]  
>  La fusion principale d'une grande quantité de données peut créer une transaction dont l'exécution est longue, ce qui retarde la troncation du journal des transactions pendant le point de contrôle. Dans ce cas, en mode de récupération complète, la taille du journal des transactions peut s'accroître considérablement. Avant de réorganiser un index de recherche en texte intégral de grande taille dans une base de données qui utilise le mode de récupération complète, il est fortement recommandé de vous assurer que votre journal des transactions contient un espace suffisant pour une transaction dont l'exécution est longue. Pour plus d’informations, consultez [Gérer la taille du fichier journal des transactions](../logs/manage-the-size-of-the-transaction-log-file.md).  
  
  
  
##  <a name="tuning-the-performance-of-full-text-indexes"></a><a name="tuning"></a>Réglage des performances des index de recherche en texte intégral  
 Pour optimiser les performances de vos index de recherche en texte intégral, appliquez les bonnes pratiques suivantes :  
  
-   Pour utiliser tous les processeurs ou cœurs au maximum, définissez [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)« `max full-text crawl ranges` » sur le nombre de processeurs sur le système. Pour plus d’informations sur cette option de configuration, consultez [Maximum de la plage de l’analyse de texte intégral (option de configuration de serveur)](../../database-engine/configure-windows/max-full-text-crawl-range-server-configuration-option.md).  
  
-   Vérifiez si la table de base a un index cluster. Utilisez un type de données entier pour la première colonne de l'index cluster. Évitez d'utiliser les GUID dans la première colonne de l'index cluster. Un remplissage multiplage sur un index cluster peut produire la vitesse de remplissage la plus élevée. Nous recommandons que la colonne servant de clé de texte intégral corresponde à un type de données Integer.  
  
-   Mettez à jour les statistiques de la table de base à l'aide de l'instruction [UPDATE STATISTICS](/sql/t-sql/statements/update-statistics-transact-sql) . Le plus important est de mettre à jour les statistiques sur l'index cluster ou la clé de texte intégral pour un remplissage complet. De cette manière, un remplissage sur plusieurs plages peut générer les partitions adéquates sur la table.  
  
-   Créez un index secondaire sur une colonne `timestamp` si vous souhaitez améliorer les performances de l'alimentation incrémentielle.  
  
-   Avant d'effectuer une alimentation complète sur un ordinateur multiprocesseur de grande capacité, nous vous recommandons de limiter temporairement la taille du pool de mémoires tampons en définissant la valeur `max server memory` de manière à laisser suffisamment de mémoire au processus fdhost.exe et au système d'exploitation. Pour plus d'informations, consultez « Estimation des besoins en mémoire du processus hôte de démon de filtre (fdhost.exe) », plus loin dans cette rubrique.  
  
  
  
##  <a name="troubleshooting-the-performance-of-full-populations"></a><a name="full"></a>Résolution des problèmes de performances des populations complètes  
 Pour diagnostiquer les problèmes de performances, consultez les journaux d'analyse de texte intégral. Pour plus d’informations sur les journaux d’analyse, consultez [Alimenter des index de recherche en texte intégral](../indexes/indexes.md).  
  
 Il est recommandé de suivre l'ordre de dépannage suivant si les performances des alimentations complètes ne sont pas satisfaisantes.  
  
### <a name="physical-memory-usage"></a>Utilisation de la mémoire physique  
 Durant une alimentation de texte intégral, fdhost.exe ou sqlservr.exe peuvent manquer partiellement ou complètement de mémoire. Si le journal d'analyse de texte intégral indique que fdhost.exe est souvent redémarré ou que le code d'erreur 8007008 est retourné, cela signifie que l'un de ces processus manque de mémoire. Si fdhost.exe produit des vidages, en particulier sur des ordinateurs multiprocesseurs de grande capacité, cela peut signifier qu'il manque de mémoire.  
  
> [!NOTE]  
>  Pour plus d’informations sur les mémoires tampons utilisées par une analyse de texte intégral, consultez [sys.dm_fts_memory_buffers &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-memory-buffers-transact-sql).  
  
 Les causes possibles sont les suivantes :  
  
-   Si la quantité de mémoire physique disponible pendant une alimentation complète est égale à zéro, le pool de mémoires tampons [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] consomme peut-être la plupart de la mémoire physique du système.  
  
     Le processus sqlservr.exe essaie de récupérer toute la mémoire disponible pour le pool de mémoires tampons, en fonction de la limite maximale de mémoire configurée pour le serveur. Si l'allocation de `max server memory` est trop importante, des insuffisances de mémoire et des échecs d'allocation de la mémoire partagée peuvent se produire pour le processus fdhost.exe.  
  
    > [!NOTE]  
    >  Durant une alimentation de texte intégral sur un ordinateur multiprocesseur, il peut se produire un conflit de mémoire au niveau du pool de mémoires tampons pour fdhost.exe ou sqlservr.exe. Le manque de mémoire partagée qui en résulte provoque des nouvelles tentatives d'exécution de lots, des surexploitations de la mémoire et des vidages par le processus fdhost.exe.  
  
     Vous pouvez résoudre ce problème en définissant de façon appropriée la valeur `max server memory` du pool de mémoires tampons [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Pour plus d'informations, consultez « Estimation des besoins en mémoire du processus hôte de démon de filtre (fdhost.exe) », plus loin dans cette rubrique. La réduction de la taille de lot utilisée pour l'indexation de texte intégral peut également s'avérer utile.  
  
-   Problème de pagination  
  
     Si la taille du fichier d'échange est insuffisante, comme cela peut se produire sur un système qui dispose d'un petit fichier d'échange avec une croissance limitée, fdhost.exe ou sqlservr.exe risquent de manquer de mémoire.  
  
     Si les journaux d'analyse n'indiquent pas de défaillances relatives à la mémoire, il est probable que les performances sont dégradées par une pagination excessive.  
  
  
  
### <a name="estimating-the-memory-requirements-of-the-filter-daemon-host-process-fdhostexe"></a>Estimation des besoins en mémoire du processus hôte de démon de filtre (fdhost.exe)  
 La quantité de mémoire requise par le processus fdhost.exe pour une alimentation dépend principalement du nombre de plages d'analyses de texte intégral utilisées, de la taille de la mémoire partagée entrante et du nombre maximal d'instances relatives à la mémoire partagée entrante.  
  
 La quantité de mémoire consommée (en octets) par l'hôte de démon de filtre peut être estimée approximativement à l'aide de la formule suivante :  
  
 *number_of_crawl_ranges* \` ism_size'*max_outstanding_isms* \* 2  
  
 Les valeurs par défaut des variables contenues dans la formule précédente sont les suivantes :  
  
|**Variable**|**Valeur par défaut**|  
|------------------|-----------------------|  
|*number_of_crawl_ranges*|Nombre de processeurs|  
|*ism_size*|1 Mo pour les ordinateurs x86<br /><br /> 4 Mo, 8 Mo ou 16 Mo pour les ordinateurs x64, en fonction de la mémoire physique totale|  
|*max_outstanding_isms*|25 pour les ordinateurs x86<br /><br /> 5 pour les ordinateurs x64|  
  
 Le tableau suivant présente des indications expliquant comment estimer les besoins en mémoire de fdhost.exe. Les formules figurant dans ce tableau utilisent les valeurs suivantes :  
  
-   *F*, qui est une évaluation de la mémoire requise par fdhost.exe (en Mo).  
  
-   *T*, qui est la mémoire physique totale disponible sur le système (en Mo).  
  
-   *M*, qui est le `max server memory` paramètre optimal.  
  
> [!IMPORTANT]  
>  Pour obtenir des informations essentielles sur les formules, voir <sup>1</sup>, <sup>2</sup>et <sup>3</sup>, ci-dessous.  
  
|Plateforme|Estimation des besoins en mémoire fdhost.exe en Mo-*F*<sup>1</sup>|Formule pour le calcul de Max Server Memory-*M*<sup>2</sup>|  
|--------------|---------------------------------------------------------------------|---------------------------------------------------------------|  
|x86|_F_ **=** _Nombre de plages d’analyse_ **&#42;** 50|_M_ **= minimum (** _T_ **,** 2000 **)- *`F`* - ** 500|  
|x64|_F_ **=** _nombre de plages d’analyse_ **&#42;** 10 **&#42;** 8|_M_ **=** _T_ **-** _F_ **-** 500|  
  
 <sup>1</sup> si plusieurs remplissages complets sont en cours, calculez les besoins en mémoire fdhost.exe de chacun séparément, par exemple *F1*, *F2*et ainsi de suite. Ensuite, calculez *M* comme _T_**-** sigma **(**_F_i **)**.  
  
 <sup>2</sup> 500 Mo sont une estimation de la mémoire requise par d’autres processus dans le système. Si le système effectue un travail supplémentaire, augmentez cette valeur en conséquence.  
  
 <sup>3</sup> . *ism_size* est supposé être de 8 Mo pour les plateformes x64.  
  
 **Exemple : estimation des besoins en mémoire de fdhost.exe**  
  
 Cet exemple se rapporte à un ordinateur AMD64 avec 8 Go de mémoire vive (RAM) et 4 processeurs double cœur. Les premières estimations de calcul de la mémoire requise par fdhost.exe : *F*. Le nombre de plages d'analyse est `8`.  
  
 `F = 8*10*8=640`  
  
 Le calcul suivant obtient la valeur optimale pour `max server memory` - *M*. *T*Le total de la mémoire physique disponible sur ce système en Mo-*t*-est `8192` .  
  
 `M = 8192-640-500=7052`  
  
 **Exemple : configuration de la mémoire maximum du serveur**  
  
 Cet exemple utilise les instructions [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) et [reconfigure](/sql/t-sql/language-elements/reconfigure-transact-sql) [!INCLUDE[tsql](../../../includes/tsql-md.md)] pour définir `max server memory` sur la valeur calculée pour *M* dans l’exemple précédent, `7052` :  
  
```  
USE master;  
GO  
EXEC sp_configure 'max server memory', 7052;  
GO  
RECONFIGURE;  
GO  
```  
  
 **Pour définir l'option de configuration max server memory**  
  
-   [server memory (options de configuration de serveur)](../../database-engine/configure-windows/server-memory-server-configuration-options.md)  
  
  
  
### <a name="factors-that-can-reduce-cpu-consumption"></a>Facteurs pouvant réduire la consommation processeur  
 Il faut s'attendre à ce que les performances des alimentations complètes ne soient pas optimales lorsque la consommation processeur moyenne est inférieure à environ 30 pour cent. Cette section traite de quelques facteurs qui affectent la consommation processeur.  
  
-   Temps d'attente élevé pour les pages  
  
     Pour savoir si un temps d'attente de page est élevé, exécutez l'instruction [!INCLUDE[tsql](../../../includes/tsql-md.md)] suivante :  
  
    ```  
    Execute SELECT TOP 10 * FROM sys.dm_os_wait_stats ORDER BY wait_time_ms DESC;  
    ```  
  
     Le tableau suivant décrit les types de temps d'attente présentant un intérêt ici.  
  
    |Type d’attente|Description|Résolution possible|  
    |---------------|-----------------|-------------------------|  
    |PAGEIO_LATCH_SH (_EX ou _UP)|Cela pourrait indiquer un goulet d'étranglement ES, auquel cas vous devriez généralement constater également une durée de file d'attente de disque moyenne élevée.|Le déplacement de l'index de recherche en texte intégral vers un groupe de fichiers différent sur un disque différent peut aider à réduire le goulet d'étranglement ES.|  
    |PAGELATCH_EX (ou _UP)|Cela pourrait indiquer beaucoup de contention parmi les threads qui essaient d'écrire dans le même fichier de base de données.|L'ajout des fichiers au groupe de fichiers sur lequel l'index de texte intégral réside pourrait aider à alléger cette contention.|  
  
     Pour plus d’informations, consultez [sys.dm_os_wait_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-wait-stats-transact-sql).  
  
-   Inefficacités dans l'analyse de la table de base  
  
     Un remplissage complet analyse la table de base pour produire des lots. Cette analyse de table peut être inefficace dans les scénarios suivantes :  
  
    -   Si la table de base a un pourcentage élevé de colonnes hors ligne qui sont indexées de texte intégral, l'analyse de la table de base pour produire des lots peut être le goulet d'étranglement. Dans ce cas, le déplacement des petites données dans la ligne à l'aide de `varchar(max)` ou `nvarchar(max)` peut améliorer la situation.  
  
    -   Si la table de base est très fragmentée, l'analyse peut être inefficace. Pour obtenir des informations sur le calcul des données hors ligne et de la fragmentation des index, consultez [sys.dm_db_partition_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-partition-stats-transact-sql) et [sys.dm_db_index_physical_stats &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql).  
  
         Pour réduire la fragmentation, vous pouvez réorganiser ou reconstruire l'index cluster. Pour plus d’informations, consultez [Réorganiser et reconstruire des index](../indexes/reorganize-and-rebuild-indexes.md).  
  
  
  
##  <a name="troubleshooting-slow-indexing-performance-due-to-filters"></a><a name="filters"></a>Résolution des problèmes de performances d’indexation lente en raison de filtres  
 Lors de l'alimentation d'un index de recherche en texte intégral, le Moteur d'indexation et de recherche en texte intégral utilise deux types de filtres : des filtres multithreads et des filtres monothreads. Certains documents, tels que les documents [!INCLUDE[msCoName](../../includes/msconame-md.md)] Word, sont filtrés à l'aide d'un filtre multithread. D'autres, tels que les documents PDF (Portable Document Format) d'Adobe Acrobat, sont filtrés à l'aide d'un filtre monothread.  
  
 Pour des raisons de sécurité, les filtres sont chargés par des processus hôtes de démon de filtre. Une instance de serveur utilise un processus multithread pour tous les filtres multithreads et un processus monothread pour tous les filtres monothreads. Lorsqu'un document qui utilise un filtre multithread contient un document incorporé qui utilise un filtre monothread, le Moteur d'indexation et de recherche en texte intégral lance un processus monothread pour le document incorporé. Par exemple, quand il rencontre un document Word qui contient un document PDF, le Moteur d’indexation et de recherche en texte intégral utilise le processus multithread pour le contenu Word et lance un processus monothread pour le contenu PDF. Toutefois, un filtre monothread peut ne pas fonctionner correctement dans cet environnement et peut déstabiliser le processus de filtrage. Dans certaines circonstances, lorsque ce type d'incorporation est courant, cette déstabilisation peut provoquer des blocages du processus de filtrage. Dans ce cas, le Moteur d'indexation et de recherche en texte intégral réachemine tout document ayant subi un échec (par exemple, un document Word avec du contenu PDF incorporé) vers le processus de filtrage monothread. Si le réacheminement a lieu fréquemment, il en résulte une détérioration des performances du processus d'indexation de texte intégral.  
  
 Pour contourner ce problème, marquez le filtre du document conteneur (Word dans le cas présent) en tant que filtre monothread. Vous pouvez modifier la valeur de Registre concernée pour marquer un filtre donné en tant que filtre monothread. Pour marquer un filtre comme filtre à thread unique, vous devez définir la valeur de Registre **ThreadingModel** pour le filtre sur `Apartment Threaded` . Pour plus d’informations sur les threads uniques cloisonnés (STA), consultez le livre blanc intitulé [Présentation et utilisation des modèles de threads COM](https://go.microsoft.com/fwlink/?LinkId=209159).  
  
  
  
## <a name="see-also"></a>Voir aussi  
 [Server Memory (options de configuration de serveur)](../../database-engine/configure-windows/server-memory-server-configuration-options.md)   
 [Max Full-Text Analysis Range (option de configuration de serveur)](../../database-engine/configure-windows/max-full-text-crawl-range-server-configuration-option.md)   
 [Remplir les index de recherche en texte intégral](populate-full-text-indexes.md)   
 [Créer et gérer des index de recherche en texte intégral](create-and-manage-full-text-indexes.md)   
 [sys. dm_fts_memory_buffers &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-memory-buffers-transact-sql)   
 [sys. dm_fts_memory_pools &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-fts-memory-pools-transact-sql)   
 [Résoudre l’indexation de texte intégral](troubleshoot-full-text-indexing.md)  
  
  
