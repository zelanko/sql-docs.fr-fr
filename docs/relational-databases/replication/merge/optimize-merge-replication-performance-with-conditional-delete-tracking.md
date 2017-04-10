---
title: "Optimiser les performances de la r&#233;plication de fusion avec le suivi conditionnel des suppressions | Microsoft Docs"
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
  - "suivi des suppressions conditionnelles [réplication SQL Server]"
  - "réplication de fusion [réplication SQL Server], suivi des suppressions conditionnelles"
  - "articles [réplication SQL Server], suivi des suppressions conditionnelles"
ms.assetid: 58f120a3-ea3a-4e97-93f0-0eb4e580ecf2
caps.latest.revision: 23
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 23
---
# Optimiser les performances de la r&#233;plication de fusion avec le suivi conditionnel des suppressions
    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 Avec la réplication de fusion, vous pouvez spécifier que les suppressions d'un ou plusieurs articles ne doivent pas faire l'objet d'un suivi par les déclencheurs de réplication et les tables système. Si vous spécifiez cette option pour un article, les suppressions ne sont pas suivies ni répliquées à partir du serveur de publication ou de quelque Abonné que ce soit. Cette option est disponible pour la prise en charge d'un certain nombre de scénarios d'application et pour l'optimisation des performances dans les cas où la réplication des suppressions n'est pas nécessaire ou souhaitable. Les performances sont améliorées de trois façons : les métadonnées des suppressions ne sont pas stockées ; les suppressions ne sont pas énumérées durant la synchronisation ; les suppressions ne sont pas répliquées sur l'Abonné, ni appliquées.  
  
> [!NOTE]  
>  Afin d'utiliser les articles en téléchargement seul, le niveau de compatibilité de la publication doit être au moins 90RTM.  
  
 Cette option peut être spécifiée lors de la création d'une publication, ou être activée ou désactivée par bascule si une application nécessite que certaines suppressions soient répliquées et d'autres pas, telles que les suppressions de traitement. Les exemples qui suivent illustrent diverses utilisations possibles de cette option dans une application :  
  
-   Une application pour une force de vente mobile possède en général des tables comme **SalesOrderHeader**, **SalesOrderDetail** et **produit**. Les commandes sont entrées au niveau de l'Abonné puis répliquées vers le serveur de publication, qui souvent fournit ces données à un système d'exécution de commandes. Beaucoup de travailleurs mobiles utilisent des périphériques portables qui ont une mémoire limitée : une fois la commande reçue par le serveur de publication, elle peut être supprimée sur l'Abonné. La suppression n'est pas propagée vers le serveur de publication, puisque cette commande est toujours active dans le système.  
  
     Dans ce scénario, les suppressions ne seraient pas suivies pour les **SalesOrderHeader** et **SalesOrderDetail** tables. Pour les suppressions seraient suivies du **produit** de table, car si un produit est supprimé du serveur de publication, la suppression doit être envoyée à l’abonné à jour la liste des produits.  
  
-   Une application peut stocker des données historiques dans une table comme **TransactionHistory**, périodiquement purgée des enregistrements antérieurs à une année. Cette table peut être filtrée de sorte que les Abonnés ne reçoivent que les données de transactions du mois en cours. Les suppressions de traitement mensuelles sur le serveur de publication purgeant les données plus anciennes ne concernent pas les Abonnés, mais sont quand même suivies et énumérées par défaut.  
  
     Dans ce scénario, avant le traitement par lots, l'activité pourrait être interrompue sur le système, et l'application pourrait désactiver le suivi des suppressions. Une fois le traitement terminé, le suivi pourrait être réactivé.  
  
> [!IMPORTANT]  
>  Si les autres activités se poursuivent sur le serveur de publication, vous devez vous assurer que les suppressions qui doivent être propagées aux Abonnés ne se produisent pas lorsque le suivi des suppressions est désactivé.  
  
 **Pour spécifier que les suppressions ne doivent pas être suivies**  
  
-   Réplication [!INCLUDE[tsql](../../../includes/tsql-md.md)] programming : [spécifier que supprime doivent pas être suivies pour fusionner les Articles & #40 ; Programmation de Transact-SQL de réplication & #41 ;](../../../relational-databases/replication/publish/specify that deletes should not be tracked for merge articles.md)  
  
## Voir aussi  
 [Options d'articles pour la réplication de fusion](../../../relational-databases/replication/merge/article-options-for-merge-replication.md)   
 [Optimiser les performances de la réplication de fusion avec les articles en téléchargement seul](../../../relational-databases/replication/merge/optimize-merge-replication-performance-with-download-only-articles.md)  
  
  