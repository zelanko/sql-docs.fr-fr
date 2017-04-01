---
title: "Optimiser les performances des filtres param&#233;tr&#233;s avec des partitions pr&#233;calcul&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "partitions précalculées [réplication SQL Server]"
  - "partitions précalculées des réplications de fusion [SQL Server replication]"
  - "fusionner des partitions précalculées de réplication [réplication SQL Server], à propos des partitions précalculées"
ms.assetid: 85654bf4-e25f-4f04-8e34-bbbd738d60fa
caps.latest.revision: 45
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# Optimiser les performances des filtres param&#233;tr&#233;s avec des partitions pr&#233;calcul&#233;es
  Les partitions précalculées représentent une optimisation des performances pouvant être utilisée avec les publications de fusion filtrées. Les partitions précalculées sont également une condition requise pour l'utilisation d'enregistrements logiques sur les publications filtrées. Pour plus d’informations sur les enregistrements logiques, consultez [modifications du groupe de lignes associées avec les enregistrements logiques](../../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md).  
  
 Lorsqu'un abonné synchronise avec un serveur de publication, ce dernier doit évaluer les filtres de l'Abonné pour déterminer quelles lignes appartiennent à la partition, ou à l'ensemble de données de cet abonné. Ce processus de détermination de l’appartenance aux partitions des modifications sur le serveur de publication pour chaque abonné recevant un dataset filtré est dénommé *d’évaluation de partition*. Sans partitions précalculées, l'évaluation de partition doit être effectuée pour chaque modification apportée à une colonne filtrée sur le serveur de publication depuis la dernière exécution de l'Agent de fusion pour un abonné spécifique, et ce processus doit être répété pour chaque abonné synchronisant avec le serveur de publication.  
  
 Toutefois, si le serveur de publication et l’abonné sont en cours d’exécution [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] ou une version ultérieure et que vous utilisez les partitions précalculées, l’appartenance de partition pour toutes les modifications sur le serveur de publication est précalculée et persistante au moment où les modifications sont apportées. Il en résulte que lorsque l'Abonné synchronise avec le serveur de publication, il peut commencer immédiatement à télécharger les modifications concernant sa partition, sans avoir à passer par le processus d'évaluation de partition. Cela peut entraîner d'importantes améliorations en terme de performance, lorsqu'une publication comporte beaucoup de modifications, d'abonnés ou d'articles dans la publication.  
  
 En plus d'utiliser des partitions précalculées, prégénérez des instantanés et/ou permettez aux Abonnés de demander la génération et l'application d'un instantané la première fois qu'ils se synchronisent. Utilisez l'une ou l'autre de ces options ou les deux pour fournir des instantanés pour les publications qui utilisent des filtres paramétrés. Si vous ne spécifiez pas une de ces options, les abonnements sont initialisés à l'aide d'une série d'instructions SELECT et INSERT au lieu d'utiliser l'utilitaire **bcp** , ce processus étant beaucoup plus lent. Pour plus d'informations, voir [Snapshots for Merge Publications with Parameterized Filters](../../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md).  
  
 **Pour utiliser les partitions précalculées**  
  
 Les partitions précalculées sont activées par défaut sur toutes les publications, nouvelles ou existantes, répondant aux conditions décrites ci-dessous. Le paramétrage peut être modifié via [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou par programme. Pour plus d’informations, consultez [optimiser les filtres de lignes paramétrable](../../../relational-databases/replication/publish/optimize-parameterized-row-filters.md).  
  
## Conditions requises à l'utilisation des partitions précalculées  
 Si les conditions requises sont atteintes, les nouvelles publications sont créées par défaut avec les partitions précalculées activées, et les publications existantes sont mises à niveau automatiquement afin d'utiliser cette fonctionnalité. Si une publication ne répond pas aux conditions requises, elle peut être modifiée pour que les partitions précalculées puissent ensuite être activées. Si quelques articles répondent aux conditions requises et d'autres non, envisagez de créer deux publications dont l'une d'entre elles est activée pour les partitions précalculées.  
  
### Conditions requises pour les clauses de filtres  
  
-   Toutes les fonctions utilisées dans le filtre de lignes paramétrable, telles que HOST_NAME() et SUSER_SNAME(), doivent apparaître directement dans la clause du filtre paramétrable et ne pas être imbriquées dans une vue ou une fonction dynamique. Pour plus d’informations sur ces fonctions, consultez la page [HOST_NAME & #40 ; Transact-SQL & #41 ;](../../../t-sql/functions/host-name-transact-sql.md), [SUSER_SNAME & #40 ; Transact-SQL & #41 ;](../../../t-sql/functions/suser-sname-transact-sql.md), et [filtres de lignes paramétrables](../../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
-   Les valeurs renvoyées pour chaque abonné ne doivent pas être modifiées une fois que la partition a été créée. Par exemple, si vous utilisez HOST_NAME() dans un filtre (sans remplacer la valeur HOST_NAME()), ne modifiez pas le nom de l'ordinateur sur l'Abonné.  
  
-   Les filtres de jointure ne doivent pas contenir de fonctions dynamiques (telles que des fonctions HOST_NAME() et SUSER_SNAME() qui évaluent à une valeur différente selon l'Abonné qui se synchronise). Seuls les filtres de lignes paramétrables doivent contenir des fonctions dynamiques.  
  
-   Les fonctions non déterministes ne peuvent pas s'utiliser dans une clause de filtre. Pour plus d'informations sur les fonctions non déterministes, consultez [Deterministic and Nondeterministic Functions](../../../relational-databases/user-defined-functions/deterministic-and-nondeterministic-functions.md).  
  
-   Les vues référencées dans les clauses de filtres de jointure ou de filtre paramétré ne doivent pas contenir de fonctions dynamiques.  
  
-   Aucune relation de filtre de jointure circulaire ne doit exister dans la publication.  
  
### Classement de base de données  
  
-   Lorsque les partitions précalculées sont utilisées, le classement de base de données est toujours utilisé lorsque des comparaisons sont effectuées, plutôt que le classement de la table ou de la colonne. Examinez le cas suivant :  
  
    -   Une base de données avec un classement respectant les accents contient une table avec un classement ne respectant pas les accents.  
  
    -   La table contient une colonne **nom_ordinateur**, qui est comparée avec le nom d’hôte de l’abonné dans un filtre paramétré.  
  
    -   La table contient une ligne avec la valeur « POSTE DE TRAVAIL » et une ligne avec la valeur « poste de travail » dans cette colonne.  
  
     Si l'Abonné synchronise avec un nom d'hôte « poste de travail », il ne reçoit qu'une ligne car la comparaison respecte les accents (le classement de la base de données). Si les partitions précalculées ne sont pas utilisées, l'Abonné reçoit les deux lignes, car la table dispose d'un classement qui ne respecte pas les accents.  
  
## Performances et partitions précalculées  
 Les partitions précalculées engendrent une légère perte de performance lorsque les modifications sont chargées de l'Abonné au serveur de publication, mais comme la majorité du temps de traitement de fusion est passé à évaluer les partitions et à charger les modifications du serveur de publication sur l'Abonné, le gain en terme de performance peut quand même s'avérer important. L'amélioration des performances peut varier en fonction du nombre d'abonnés synchronisant simultanément, et le nombre de mises à jour par synchronisation déplaçant les lignes d'une partition à l'autre.  
  
## Voir aussi  
 [Filtres de lignes paramétrés](../../../relational-databases/replication/merge/parameterized-row-filters.md)  
  
  