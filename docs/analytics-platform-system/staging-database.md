---
title: Créer la base de données intermédiaire Parallel Data Warehouse
author: barbkess
ms.author: barbkess
manager: craigg
ms.prod: analytics-platform-system
ms.prod_service: mpp-data-warehouse
ms.service: ''
ms.component: ''
ms.suite: sql
ms.custom: ''
ms.technology: mpp-data-warehouse
description: SQL Server Parallel Data Warehouse (PDW) utilise une base de données intermédiaire pour stocker des données temporairement pendant le processus de chargement.
ms.date: 10/20/2016
ms.topic: article
ms.assetid: 6d0b2726-4772-4858-b700-885cc12219b2
caps.latest.revision: 20
ms.openlocfilehash: c85a2490f9c74839f795a1dffab106f9a92c528c
ms.sourcegitcommit: 9351e8b7b68f599a95fb8e76930ab886db737e5f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2018
---
# <a name="staging-database"></a>Base de données intermédiaire 
SQL Server Parallel Data Warehouse (PDW) utilise une base de données intermédiaire pour stocker des données temporairement pendant le processus de chargement. Par défaut, SQL Server PDW utilise la base de données de destination en tant que la base de données intermédiaire qui peut causer une fragmentation de la table. Pour réduire la fragmentation de la table, vous pouvez créer une base de données mise en lots défini par l’utilisateur. Ou bien, lors de la restauration à partir d’un échec de chargement n’est pas un problème, vous pouvez utiliser le mode de chargement de fastappend pour améliorer les performances par la non-exécution de la table temporaire et de charger directement dans la table de destination.  
  
## <a name="StagingDatabase"></a>Concepts de base de mise en lots  
A *base de données intermédiaire* est créé par l’utilisateur PDW base de données qui stocke les données temporairement pendant son chargement dans l’appliance. Lorsqu’une base de données intermédiaire est spécifié pour une charge, l’appliance tout d’abord copie les données à la base de données mise en lots et copie ensuite les données à partir de tables temporaires dans la zone de transit de la base de données à des tables permanentes dans la base de données de destination.  
  
Lorsqu’une base de données intermédiaire n’est pas spécifié pour une charge, SQL ServerPDW crée les tables temporaires dans la base de données de destination et les utilise pour stocker les données chargées avant d’insérer les données chargées dans les tables de destination définitive.  
  
Lorsqu’une charge utilise le *fastappend mode*, SQL ServerPDW ignore complètement à l’aide de tables temporaires et ajoute les données directement à la table cible. Le mode fastappend améliore les performances de chargement pour les scénarios ELT où les données sont chargées dans une table qui est une table temporaire à partir du point de vue de l’application. Par exemple, un processus ELT peut charger des données dans une table temporaire, traiter les données en dédupliquant et nettoyage, puis insérez les données dans la table de faits cible. Dans ce cas, il n’est pas nécessaire pour PDW à charger en premier les données dans une table temporaire interne avant d’insérer les données dans la table temporaire de l’application. Le mode fastappend permet d’éviter l’étape de la charge supplémentaire, qui améliore considérablement les performances de la charge. Notez que pour utiliser le mode fastappend, vous devez utiliser en mode de transaction multiples, ce qui signifie que la récupération à partir d’un échec ou abandon de charge doit être gérée par votre propre processus de chargement.  
  
**Avantages de la base de données de mise en lots**  
  
Le principal avantage d’une base de données intermédiaire est de réduire la fragmentation de la table. Si une base de données intermédiaire n’est pas utilisé, les données sont chargées dans des tables temporaires dans la base de données de destination. Lorsque les tables temporaires obtient créés et supprimés dans la base de données de destination, les pages pour les tables temporaires et les tables permanentes deviennent entrelacées. Au fil du temps, cela provoque la fragmentation de table et dégrade les performances. En revanche, une base de données mise en lots permet de s’assurer que les tables temporaires sont créés et supprimés dans un espace de fichier distinct à des tables permanentes.  
  
**Structures de table de base de données mise en lots**  
  
La structure de stockage pour chaque table de base de données dépend de la table de destination.  
  
-   Pour les charges dans un segment de mémoire ou un index columnstore en cluster, la table intermédiaire est un segment de mémoire.  
  
-   Pour les charges dans un index cluster rowstore, la table intermédiaire est un index cluster rowstore.  
  
## <a name="Permissions"></a>Permissions  
Nécessite l’autorisation de créer (pour créer une table temporaire) sur la base de données mise en lots. 

<!-- MISSING LINKS

For more information, see [Grant Permissions to load data](grant-permissions-to-load-data.md).  

-->
  
## <a name="CreatingStagingDatabase"></a>Meilleures pratiques pour la création d’une base de données mise en lots  
  
1.  Doit être une base de données intermédiaire par appliance. Cela peut être partagé par tous les travaux de chargement pour toutes les bases de données de destination.  
  
2.  La taille de la base de données intermédiaire est spécifique au client. Au départ, lors du remplissage d’abord l’application, la base de données intermédiaire doit être suffisamment grand pour contenir les travaux de chargement initial. Chargement des tâches ont tendance à être volumineux, car plusieurs chargements peuvent se produire simultanément. Une fois les travaux de chargement initial est terminé et que le système est en production, la taille de chaque charge de travail est susceptible d’être plus petite. Lorsque cela se produit, vous pouvez réduire la taille de la base de données mise en lots pour prendre en compte la plus petite taille de charge. Pour réduire la taille, vous pouvez supprimer la base de données mise en lots et créer à nouveau avec des allocations plus petites de taille, ou vous pouvez utiliser la [ALTER DATABASE](../t-sql/statements/alter-database-parallel-data-warehouse.md) instruction.  
  
    Lorsque vous créez la base de données mise en lots, utilisez les instructions suivantes.  
  
    -   La taille de la table répliquée doit être la taille estimée par nœud de calcul, de toutes les tables répliquées chargera simultanément. Il s’agit généralement de 25 à 30 Go.  
  
    -   La taille de la table distribuée doit être la taille estimée par appliance, de toutes les tables distribuées chargera simultanément.  
  
    -   La taille du journal est généralement similaire à la taille de la table répliquée.  
  
## <a name="Examples"></a>Exemples  
  
### <a name="a-create-a-staging-database"></a>A. Créer une base de données mise en lots 
L’exemple suivant crée une base de données intermédiaire, Stagedb, pour une utilisation avec toutes les charges de l’appliance. Supposons que vous estimez que cinq répliquées des tables de taille de que 5 Go chargera simultanément. Cela entraîne l’allocation d’au moins 25 Go pour la taille répliquée. Supposons que vous estimez que six distribué des tables de tailles 100, 200, 400, 500, 500 et 550 Go chargera simultanément. Cela entraîne l’allocation au moins 2250 Go pour la taille de la table distribuée.  
  
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
  
