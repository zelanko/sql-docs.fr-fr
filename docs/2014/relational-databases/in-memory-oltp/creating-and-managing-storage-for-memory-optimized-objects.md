---
title: Création et gestion du stockage des objets mémoire optimisés | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 622aabe6-95c7-42cc-8768-ac2e679c5089
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 1d6bb42e4b35a74ef2bd6eefb85ea81b0ed18e40
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63073844"
---
# <a name="creating-and-managing-storage-for-memory-optimized-objects"></a>Création et gestion du stockage des objets mémoire optimisés
  Le moteur [!INCLUDE[hek_2](../../includes/hek-2-md.md)] est intégré dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], ce qui vous permet d’avoir des tables optimisées en mémoire et des tables sur disque (traditionnelles) dans la même base de données. Toutefois, la structure de stockage des tables optimisées en mémoire est différente de celle des tables sur disque.  
  
 Les principales caractéristiques du stockage des tables sur disque sont les suivantes :  
  
-   Elles sont mappées à groupe de fichiers contenant un ou plusieurs fichiers.  
  
-   Chaque fichier est divisé en étendues de 8 pages de 8 Ko chacune.  
  
-   Une étendue peut être partagée entre plusieurs tables, mais il existe une correspondance univoque entre une page allouée et la table ou l’index. En d’autres termes, une page ne peut pas contenir de lignes issues de plusieurs tables ou index.  
  
-   Les données sont placées dans la mémoire (le pool de mémoires tampons) en fonction des besoins et les pages modifiées ou créées sont écrites de façon asynchrone sur le disque, générant essentiellement des E/S aléatoires.  
  
 Les principales caractéristiques du stockage des tables optimisées en mémoire sont les suivantes :  
  
-   Toutes les tables mémoire optimisées sont mappées à un groupe de fichiers mémoire optimisé. Ce groupe de fichiers est créé à l'aide du groupe de fichiers de flux de fichier.  
  
-   Il n’y a aucune page et les données sont conservées sur une ligne.  
  
-   Toutes les modifications apportées aux tables optimisées en mémoire sont stockées à la fin des fichiers actifs. La lecture et l’écriture des fichiers sont séquentielles.  
  
-   Une mise à jour correspond à une suppression suivie d’une insertion. Les lignes supprimées ne sont pas immédiatement supprimées du stockage. Les lignes supprimées le sont par un processus d’arrière-plan, appelé MERGE, basé sur une stratégie et décrit dans [Durabilité pour les tables optimisées en mémoire](memory-optimized-tables.md).  
  
-   Contrairement aux tables sur disque, le stockage des tables optimisées en mémoire n’est pas compressé. Lors de la migration d’une table sur disque (ligne ou page) compressée vers une table optimisée en mémoire, vous devez prendre en compte la modification de taille.  
  
-   Une table optimisée en mémoire peut être durable ou non durable. Vous devez simplement configurer le stockage des tables mémoire optimisées durables.  
  
 Cette section décrit les paires de fichiers de point de contrôle d'autres aspects du stockage des données dans des tables mémoire optimisées.  
  
 Rubriques de cette section :  
  
-   [Configuration du stockage des tables à mémoire optimisée](configuring-storage-for-memory-optimized-tables.md)  
  
-   [Groupe de fichiers mémoire optimisé](the-memory-optimized-filegroup.md)  
  
-   [Durabilité pour les tables optimisées en mémoire](memory-optimized-tables.md)  
  
-   [Opération de point de contrôle pour les tables mémoire optimisées](checkpoint-operation-for-memory-optimized-tables.md)  
  
-   [Définition de la durabilité des objets mémoire optimisés](defining-durability-for-memory-optimized-objects.md)  
  
-   [Comparaison du stockage des tables sur disque et du stockage des tables à mémoire optimisée](comparing-disk-based-table-storage-to-memory-optimized-table-storage.md)  
  
-   [Surveiller et dépanner la fusion de paires de fichiers de données et de fichiers delta](../../database-engine/monitoring-and-troubleshooting-merge-for-data-and-delta-file-pairs.md)  
  
## <a name="see-also"></a>Voir aussi  
 [OLTP en mémoire &#40;Optimisation en mémoire&#41;](in-memory-oltp-in-memory-optimization.md)  
  
  
