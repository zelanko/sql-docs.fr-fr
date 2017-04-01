---
title: "Propri&#233;t&#233;s de publication, Partitions de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newpubwizard.pubproperties.datapartitions.f1"
ms.assetid: 5869edb7-d05f-495b-b828-b7fd5e828d20
caps.latest.revision: 20
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 20
---
# Propri&#233;t&#233;s de publication, Partitions de donn&#233;es
  La page **Partitions de données** de la boîte de dialogue **Propriétés de la publication** permet de définir des partitions de données pour les publications de fusion qui utilisent le filtrage paramétré. Après avoir défini les partitions, vous pouvez générer des instantanés pour fournir différents jeux de données initiaux pour différents abonnés en fonction des propriétés de connexion (connexion et/ou nom d'ordinateur) des abonnés. Vous pouvez également permettre aux abonnés de demander la distribution et la génération d'instantanés s'ils ne disposent pas d'un instantané pour leur partition lorsqu'ils se synchronisent pour la première fois. Pour plus d'informations, voir [Create a Snapshot for a Merge Publication with Parameterized Filters](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).  
  
## Options  
 **Ajouter**  
 Cliquez sur **Ajouter** pour définir une partition. Dans le **Ajouter une Partition de données** boîte de dialogue, spécifiez les valeurs pour **HOST_NAME()** et/ou **SUSER_SNAME()**, et définir une planification d’actualisation des instantanés.  
  
 **Modifier**  
 Sélectionnez une partition existante dans la grille, puis cliquez sur **Modifier** pour modifier la partition.  
  
 **Delete**  
 Sélectionnez une partition existante dans la grille, puis cliquez sur **Supprimer** pour supprimer la partition.  
  
 **Générer les instantanés sélectionnés maintenant**  
 Sélectionnez une ou plusieurs partitions dans la grille, puis cliquez sur **Générer les instantanés sélectionnés maintenant** pour générer des instantanés pour ces partitions.  
  
 **Nettoyer les instantanés existants**  
 Sélectionnez une ou plusieurs partitions dans la grille, puis cliquez sur **Nettoyer les instantanés existants** pour nettoyer les instantanés pour ces partitions.  
  
 **Définir automatiquement une partition et générer un instantané si nécessaire lorsqu'un nouvel abonné essaie de se synchroniser**  
 Sélectionnez cette option si vous voulez permettre aux abonnés de demander la génération et l'application d'instantanés. Les abonnés peuvent avoir besoin de cette option s'ils ne disposent pas d'un instantané pour leur partition lorsqu'ils se synchronisent pour la première fois.  
  
## Voir aussi  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Afficher et modifier les propriétés d'une publication](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Filtres de lignes paramétrés](../../relational-databases/replication/merge/parameterized-row-filters.md)   
 [Publier des données et des objets de base de données](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Instantanés des publications de fusion avec des filtres paramétrés](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md)  
  
  