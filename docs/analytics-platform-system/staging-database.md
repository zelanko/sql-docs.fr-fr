---
title: À l’aide d’une base de données intermédiaire - Parallel Data Warehouse | Microsoft Docs
description: SQL Server Parallel Data Warehouse (PDW) utilise une base de données intermédiaire pour stocker des données temporairement pendant le processus de chargement.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 52ede16185515c3df00ff21ece784d62eec984ef
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63157689"
---
# <a name="using-a-staging-database-in-parallel-data-warehouse-pdw"></a>À l’aide d’une base de données intermédiaire dans Parallel Data Warehouse (PDW)
SQL Server Parallel Data Warehouse (PDW) utilise une base de données intermédiaire pour stocker des données temporairement pendant le processus de chargement. Par défaut, SQL Server PDW utilise la base de données de destination en tant que la base de données intermédiaire, ce qui peut entraîner la fragmentation des tables. Pour réduire la fragmentation de la table, vous pouvez créer une base de données mise en lots définie par l’utilisateur. Ou bien, lors de la restauration à partir d’un échec de chargement n’est pas un problème, vous pouvez utiliser le mode de chargement de fastappend pour améliorer les performances en ignorant la table temporaire et de chargement directement dans la table de destination.  
  
## <a name="StagingDatabase"></a>Principes de base de base de données mise en lots  
Un *base de données intermédiaire* est une base PDW créés par l’utilisateur qui stocke les données temporairement pendant son chargement dans l’appliance. Lorsqu’une base de données intermédiaire est spécifié pour une charge, l’appliance tout d’abord copie les données dans la base de données intermédiaire et copie ensuite les données à partir de tables temporaires dans la zone de transit de la base de données aux tables permanentes dans la base de données de destination.  
  
Lorsqu’une base de données intermédiaire n’est pas spécifié pour une charge, SQL ServerPDW crée les tables temporaires dans la base de données de destination et les utilise pour stocker les données chargées avant d’insérer les données chargées dans les tables de destination définitive.  
  
Quand une charge utilise le *en mode fastappend*, SQL ServerPDW ignore complètement à l’aide de tables temporaires et ajoute les données directement à la table cible. Le mode fastappend améliore les performances de charge pour les scénarios ELT où les données sont chargées dans une table qui est une table temporaire à partir du point de vue de l’application. Par exemple, un processus ELT peut charger des données dans une table temporaire, traiter les données au nettoyage et dédupliquant, puis insérez les données dans la table de faits cible. Dans ce cas, il n’est pas nécessaire pour PDW commencer par charger les données dans une table temporaire interne avant d’insérer les données dans la table temporaire de l’application. Le mode fastappend évite l’étape de charge supplémentaire, ce qui améliore considérablement les performances de chargement. Pour utiliser le mode fastappend, vous devez utiliser le mode de transaction multiples, ce qui signifie que la récupération à partir d’une charge de l’échec ou abandonnée doit être gérée par votre propre processus de chargement.  
  
**Avantages de la base de données de mise en lots**  
  
Le principal avantage d’une base de données intermédiaire consiste à réduire la fragmentation de la table. Si une base de données intermédiaire n’est pas utilisé, les données sont chargées dans des tables temporaires dans la base de données de destination. Lorsque les tables temporaires ainsi créés et supprimés dans la base de données de destination, les pages pour les tables temporaires et les tables permanentes deviennent entrelacées. Au fil du temps, la fragmentation de la table se produit et dégrade les performances. En revanche, une base de données mise en lots permet de s’assurer que les tables temporaires sont créés et supprimés dans un espace de fichier distinct à des tables permanentes.  
  
**Structures de table de base de données mise en lots**  
  
La structure de stockage pour chaque table de base de données dépend de la table de destination.  
  
-   Pour les charges dans un segment de mémoire ou d’un index cluster columnstore, la table intermédiaire est un segment de mémoire.  
  
-   Pour les charges dans un index cluster rowstore, la table intermédiaire est un index cluster rowstore.  
  
## <a name="Permissions"></a>Permissions  
Nécessite l’autorisation de créer (pour la création d’une table temporaire) sur la base de données intermédiaire. 

<!-- MISSING LINKS

For more information, see [Grant Permissions to load data](grant-permissions-to-load-data.md).  

-->
  
## <a name="CreatingStagingDatabase"></a>Meilleures pratiques pour la création d’une base de données intermédiaire  
  
1.  Il ne doit exister qu’une base de données intermédiaire par appliance. La base de données intermédiaire peut être partagé par tous les travaux de charge pour toutes les bases de données de destination.  
  
2.  La taille de la base de données intermédiaire est spécifique au client. Au départ, lors du remplissage tout d’abord l’appliance, la base de données intermédiaire doit être suffisamment grand pour prendre en charge les tâches de la charge initiale. Chargement des tâches ont tendance à être volumineux, car plusieurs chargements peuvent se produire simultanément. Après la fin des travaux de la charge initiale et le système est en production, la taille de chaque charge de travail est susceptible d’être plus petits. Lorsque les charges sont petits, vous pouvez réduire la taille de la base de données mise en lots pour prendre en compte la charge de petite taille. Pour réduire la taille, vous pouvez supprimer la base de données intermédiaire et recréez-le avec des allocations de taille plus petites, ou vous pouvez utiliser la [ALTER DATABASE](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw) instruction.  
  
    Lorsque vous créez la base de données intermédiaire, utilisez les instructions suivantes.  
  
    -   La taille de la table répliquée doit être la taille estimée par nœud de calcul, de toutes les tables répliquées qui chargera simultanément. La taille est généralement 25 à 30 Go.  
  
    -   La taille de la table distribuée doit être la taille estimée par appliance, de toutes les tables distribuées chargera simultanément.  
  
    -   La taille du journal ressemble généralement à la taille de la table répliquée.  
  
## <a name="Examples"></a>Exemples  
  
### <a name="a-create-a-staging-database"></a>A. Créer une base de données intermédiaire 
L’exemple suivant crée une base de données intermédiaire, Stagedb, pour une utilisation avec tous les chargements sur l’appliance. Supposons que vous estimez que cinq répliquées des tables de taille de que 5 Go chargera simultanément. Cette concurrence entraîne l’allocation d’au moins 25 Go pour la taille répliquée. Supposons que vous estimez que six distribué des tables de tailles 100, 200, 400, 500, 500 et 550 Go chargera simultanément. Cette concurrence entraîne allouer au moins 2250 Go pour la taille de la table distribuée.  
  
```sql  
CREATE DATABASE Stagedb  
WITH (  
  
    AUTOGROW = ON,  
  
    REPLICATED_SIZE = 25 GB,  
  
    DISTRIBUTED_SIZE = 2250 GB,  
  
    LOG_SIZE = 25 GB  
  
);  
```  

<!-- MISSING LINKS
 
## See Also  
[Common metadata query examples](metadata-query-examples.md)  

-->
  
