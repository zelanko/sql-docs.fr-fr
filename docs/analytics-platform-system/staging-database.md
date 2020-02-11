---
title: Utilisation d’une base de données intermédiaire
description: SQL Server Parallel Data Warehouse (PDW) utilise une base de données de mise en lots pour stocker temporairement les données pendant le processus de chargement.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: dcd7f95833695cc5f9f791d83a6221c35e88f58e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "74400284"
---
# <a name="using-a-staging-database-in-parallel-data-warehouse-pdw"></a>Utilisation d’une base de données intermédiaire en parallèle Data Warehouse (PDW)
SQL Server Parallel Data Warehouse (PDW) utilise une base de données de mise en lots pour stocker temporairement les données pendant le processus de chargement. Par défaut, SQL Server PDW utilise la base de données de destination en tant que base de données de mise en lots, ce qui peut entraîner une fragmentation de la table. Pour réduire la fragmentation des tables, vous pouvez créer une base de données intermédiaire définie par l’utilisateur. Ou, lorsque la restauration à partir d’un échec de chargement n’est pas un problème, vous pouvez utiliser le mode de chargement fastappend pour améliorer les performances en ignorant la table temporaire et en chargeant directement dans la table de destination.  
  
## <a name="StagingDatabase"></a>Notions de base des bases de données intermédiaires  
Une *base de données intermédiaire* est une base de données PDW créée par l’utilisateur, qui stocke temporairement les données pendant leur chargement dans l’appliance. Lorsqu’une base de données de mise en lots est spécifiée pour une charge, l’appliance copie d’abord les données dans la base de données intermédiaire, puis copie les données des tables temporaires dans la base de données de mise en lots vers des tables permanentes dans la base de données de destination.  
  
Lorsqu’une base de données de mise en lots n’est pas spécifiée pour une charge, SQL ServerPDW crée les tables temporaires dans la base de données de destination et les utilise pour stocker les données chargées avant d’insérer les données chargées dans les tables de destination permanentes.  
  
Quand une charge utilise le *mode fastappend*, SQL ServerPDW ignore l’utilisation des tables temporaires et ajoute les données directement à la table cible. Le mode fastappend améliore les performances de chargement pour les scénarios ELT où les données sont chargées dans une table qui est une table temporaire du point de vue de l’application. Par exemple, un processus ELT peut charger des données dans une table temporaire, traiter les données par nettoyage et duping, puis insérer les données dans la table de faits cible. Dans ce cas, il n’est pas nécessaire pour PDW de charger d’abord les données dans une table temporaire interne avant d’insérer les données dans la table temporaire de l’application. Le mode fastappend évite l’étape de chargement supplémentaire, ce qui améliore considérablement les performances de chargement. Pour utiliser le mode fastappend, vous devez utiliser le mode multi-transaction, ce qui signifie que la récupération à partir d’un échec ou d’une charge abandonnée doit être gérée par votre propre processus de chargement.  
  
**Avantages de la base de données intermédiaire**  
  
L’avantage principal d’une base de données de mise en lots est de réduire la fragmentation des tables. Si une base de données de mise en lots n’est pas utilisée, les données sont chargées dans les tables temporaires de la base de données de destination. Lorsque des tables temporaires sont créées et supprimées dans la base de données de destination, les pages pour les tables temporaires et les tables permanentes sont entrelacées. Au fil du temps, la fragmentation des tables se produit et dégrade les performances. En revanche, une base de données de mise en lots garantit que les tables temporaires sont créées et supprimées dans un espace de fichier distinct de celui des tables permanentes.  
  
**Structures de la table de base de données intermédiaire**  
  
La structure de stockage pour chaque table de base de données dépend de la table de destination.  
  
-   Pour les chargements dans un segment de mémoire ou un index ColumnStore cluster, la table de mise en lots est un segment de mémoire.  
  
-   Pour les chargements dans un index cluster rowstore, la table de mise en lots est un index cluster rowstore.  
  
## <a name="Permissions"></a>Autorisations  
Nécessite l’autorisation CREATe (pour créer une table temporaire) sur la base de données de mise en lots. 

<!-- MISSING LINKS

For more information, see [Grant Permissions to load data](grant-permissions-to-load-data.md).  

-->
  
## <a name="CreatingStagingDatabase"></a>Meilleures pratiques pour la création d’une base de données de mise en lots  
  
1.  Il ne doit y avoir qu’une seule base de données intermédiaire par appliance. La base de données intermédiaire peut être partagée par toutes les tâches de chargement de toutes les bases de données de destination.  
  
2.  La taille de la base de données de mise en lots est spécifique au client. Au départ, lors du premier remplissage de l’appliance, la base de données intermédiaire doit être suffisamment grande pour accueillir les travaux de chargement initiaux. Ces tâches de chargement ont tendance à être volumineuses, car plusieurs charges peuvent se produire simultanément. Une fois les travaux de chargement initiaux terminés et le système en production, la taille de chaque travail de chargement est susceptible d’être plus petite. Lorsque les chargements sont faibles, vous pouvez réduire la taille de la base de données intermédiaire pour prendre en charge les plus petites tailles de charge. Pour réduire la taille, vous pouvez supprimer la base de données de mise en lots et la recréer avec des allocations de plus petite taille, ou vous pouvez utiliser l’instruction [ALTER DATABASE](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw) .  
  
    Lorsque vous créez la base de données intermédiaire, suivez les instructions ci-dessous.  
  
    -   La taille de la table répliquée doit être la taille estimée, par nœud de calcul, de toutes les tables répliquées qui seront chargées simultanément. La taille est généralement de 25-30 Go.  
  
    -   La taille de la table distribuée doit être la taille estimée, par appliance, de toutes les tables distribuées qui seront chargées simultanément.  
  
    -   La taille du journal est généralement similaire à la taille de la table répliquée.  
  
## <a name="Examples"></a>Exemples  
  
### <a name="a-create-a-staging-database"></a>R. Créer une base de données de mise en lots 
L’exemple suivant crée une base de données de mise en lots, Stagedb, à utiliser avec toutes les charges sur l’appliance. Supposons que vous estimez que cinq tables répliquées d’une taille de 5 Go chacune sera chargée simultanément. Cette concurrence entraîne l’allocation d’au moins 25 Go pour la taille répliquée. Supposons que vous estimez que six tables distribuées de tailles 100, 200, 400, 500, 500 et 550 Go se chargent simultanément. Cette concurrence entraîne l’allocation d’au moins 2250 Go pour la taille de la table distribuée.  
  
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
  
