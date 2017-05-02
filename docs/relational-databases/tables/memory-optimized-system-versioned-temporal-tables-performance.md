---
title: "Performances des tables temporelles optimisées en mémoire avec gestion de version par le système | Microsoft Docs"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/28/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-tables
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e110984-7703-4806-a24b-b41e8c3018c6
caps.latest.revision: 14
author: CarlRabeler
ms.author: carlrab
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: d67b2ac2eb3f10bd5ecbf973ec97d12566973738
ms.lasthandoff: 04/11/2017

---
# <a name="memory-optimized-system-versioned-temporal-tables-performance"></a>Performances des tables temporelles optimisées en mémoire avec gestion de version par le système
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  Cette rubrique décrit certaines considérations relatives aux performances lors de l’utilisation de tables temporelles optimisées en mémoire avec gestion de version par le système.  
  
-   L’ajout de la gestion de version à une table non temporelle a un impact sur les opérations de mise à jour et de suppression, car la table historique est mise à jour automatiquement.  
  
-   Chaque mise à jour et chaque suppression sont enregistrées dans la table historique interne optimisée en mémoire. Vous pouvez donc constater une consommation importante de mémoire, si votre charge de travail exécute ces deux opérations massivement. Par conséquent, voici ce que nous vous conseillons :  
  
    -   N’effectuez pas de suppressions massives de la table actuelle afin d’augmenter la mémoire vive disponible par un nettoyage de l’espace. Envisagez de supprimer les données en plusieurs lots par un vidage manuel intermédiaire, en appelant [sp_xtp_flush_temporal_history](../../relational-databases/system-stored-procedures/temporal-table-sp-xtp-flush-temporal-history.md)ou pendant **SYSTEM_VERSIONING = OFF**.  
  
    -   Ne mettez pas à jour de nombreuses tables, car cela peut entraîner une consommation de mémoire deux fois supérieure à celle requise pour mettre à jour une table non temporelle optimisée en mémoire. Cette consommation de mémoire double est temporaire, car la tâche de vidage des données cherche régulièrement à maintenir la consommation de mémoire de la table interne de mise en lots dans les limites de l’état stable (environ 10 % de la consommation de mémoire de la table temporelle actuelle). Envisagez d’effectuer des mises à jour massives en plusieurs lots ou pendant **SYSTEM_VERSIONING = OFF**, comme pour définir les valeurs par défaut des nouvelles colonnes ajoutées.  
  
-   La période d’activation de la tâche de vidage des données n’est pas configurable, mais vous pouvez exécuter le processus en appelant [sp_xtp_flush_temporal_history](../../relational-databases/system-stored-procedures/temporal-table-sp-xtp-flush-temporal-history.md).  
  
-   Envisagez d’utiliser l’index columnstore en cluster comme option de stockage pour la table historique sur disque, notamment si vous prévoyez d’exécuter des requêtes d’analyse sur des données historiques qui utilisent des fonctions d’agrégation ou de fenêtrage. Dans ce cas, l’index columnstore en cluster sera le meilleur choix pour la table historique, car il assure une bonne compression des données et facilite les insertions d’une manière compatible avec le mode de génération des données historiques.  
  
## <a name="did-this-article-help-you-were-listening"></a>Cet article vous a-t-il été utile ? Nous sommes à votre écoute  
 Quels renseignements souhaitez-vous obtenir ? Avez-vous trouvé ce que vous cherchiez ? Nous tenons compte de vos commentaires pour améliorer le contenu de nos articles. Veuillez envoyer vos commentaires à l’adresse suivante : [sqlfeedback@microsoft.com](mailto:sqlfeedback@microsoft.com?subject=Your%20feedback%20about%20the%20Performance%20Considerations%20with%20Memory-Optimized%20System-Versioned%20Temporal%20Tables%20page)  
  
## <a name="see-also"></a>Voir aussi  
 [Tables temporelles à système par version avec tables optimisées en mémoire](../../relational-databases/tables/system-versioned-temporal-tables-with-memory-optimized-tables.md)   
 [Création d’une table temporelle optimisée en mémoire avec gestion de versions par le système](../../relational-databases/tables/creating-a-memory-optimized-system-versioned-temporal-table.md)   
 [Utilisation des tables temporelles optimisées en mémoire avec gestion de version par le système](../../relational-databases/tables/working-with-memory-optimized-system-versioned-temporal-tables.md)   
 [Surveillance des tables temporelles optimisées en mémoire avec gestion de versions par le système](../../relational-databases/tables/monitoring-memory-optimized-system-versioned-temporal-tables.md)   
 [Tables temporelles](../../relational-databases/tables/temporal-tables.md)   
 [Vérifications de cohérence système des tables temporelles](../../relational-databases/tables/temporal-table-system-consistency-checks.md)   
 [Gérer la rétention des données d’historique dans les tables temporelles avec version gérée par le système](../../relational-databases/tables/manage-retention-of-historical-data-in-system-versioned-temporal-tables.md)   
 [Vues et fonctions de métadonnées de table temporelle](../../relational-databases/tables/temporal-table-metadata-views-and-functions.md)  
  
  

