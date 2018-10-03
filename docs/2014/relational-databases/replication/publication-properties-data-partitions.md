---
title: Propriétés de publication, Partitions de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.pubproperties.datapartitions.f1
ms.assetid: 5869edb7-d05f-495b-b828-b7fd5e828d20
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: df90abfc372d583269152a7cbfe8ab0d5bebf34d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48211259"
---
# <a name="publication-properties-data-partitions"></a>Propriétés de publication, Partitions de données
  La page **Partitions de données** de la boîte de dialogue **Propriétés de la publication** permet de définir des partitions de données pour les publications de fusion qui utilisent le filtrage paramétré. Après avoir défini les partitions, vous pouvez générer des instantanés pour fournir différents jeux de données initiaux pour différents abonnés en fonction des propriétés de connexion (connexion et/ou nom d'ordinateur) des abonnés. Vous pouvez également permettre aux abonnés de demander la distribution et la génération d'instantanés s'ils ne disposent pas d'un instantané pour leur partition lorsqu'ils se synchronisent pour la première fois. Pour plus d'informations, voir [Créer un instantané d'une publication de fusion avec des filtres paramétrés](create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).  
  
## <a name="options"></a>Options  
 **Ajouter**  
 Cliquez sur **Ajouter** pour définir une partition. Dans la boîte de dialogue **Ajouter une partition de données** , définissez les valeurs de **HOST_NAME()** et/ou de **SUSER_SNAME()** et spécifiez une planification d'actualisation des instantanés.  
  
 **Modifier**  
 Sélectionnez une partition existante dans la grille et cliquez sur **Modifier** pour modifier la partition.  
  
 **Supprimer**  
 Sélectionnez une partition existante dans la grille et cliquez sur **Supprimer** pour supprimer la partition.  
  
 **Générer les instantanés sélectionnés maintenant**  
 Sélectionnez une ou plusieurs partitions dans la grille et cliquez sur **Générer les instantanés sélectionnés maintenant** pour générer des instantanés pour ces partitions.  
  
 **Nettoyer les instantanés existants**  
 Sélectionnez une ou plusieurs partitions dans la grille et cliquez sur **Nettoyer les instantanés existants** pour nettoyer les instantanés pour ces partitions.  
  
 **Définir automatiquement une partition et générer un instantané si nécessaire lorsqu'un nouvel abonné essaie de se synchroniser**  
 Sélectionnez cette option si vous voulez permettre aux abonnés de demander la génération et l'application d'instantanés. Les abonnés peuvent avoir besoin de cette option s'ils ne disposent pas d'un instantané pour leur partition lorsqu'ils se synchronisent pour la première fois.  
  
## <a name="see-also"></a>Voir aussi  
 [Create a Publication](publish/create-a-publication.md)   
 [Afficher et modifier les propriétés d’une publication](publish/view-and-modify-publication-properties.md)   
 [Parameterized Row Filters](merge/parameterized-filters-parameterized-row-filters.md)   
 [Publier des données et des objets de base de données](publish/publish-data-and-database-objects.md)   
 [Instantanés des publications de fusion avec des filtres paramétrés](snapshots-for-merge-publications-with-parameterized-filters.md)  
  
  
