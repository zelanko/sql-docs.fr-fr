---
title: Agent d’instantané (Assistant Nouvelle publication) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newpubwizard.configuresnapshotagent.f1
ms.assetid: 0257d4ee-1f7b-49fd-b4ef-65bfc1ef6951
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 20e4e015064dcf0e472c2f3c56ecabf4100e6fe7
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62676580"
---
# <a name="snapshot-agent-new-publication-wizard"></a>Agent d'instantané (Assistant Nouvelle publication)
  L'Agent d'instantané crée des fichiers qui contiennent le schéma de publication et les données utilisées pour initialiser de nouveaux abonnements. Par défaut, il s'exécute immédiatement après la création de la publication dans l'Assistant Nouvelle publication. Par la suite, il s'exécute selon une planification spécifiée. La création de nouveaux fichiers d'instantané par l'agent à chaque exécution dépend du type de réplication et des options choisies. Pour plus d’informations, consultez [Créer et appliquer un instantané](create-and-apply-the-snapshot.md).  
  
 Pour les publications de fusion utilisant les filtres paramétrés, vous devez créer un instantané pour chaque partition de données après la fin de l'instantané pour la publication. Pour plus d'informations, voir [Snapshots for Merge Publications with Parameterized Filters](snapshots-for-merge-publications-with-parameterized-filters.md).  
  
## <a name="options"></a>Options  
 **Créer un instantané immédiatement** (réplication de fusion) ou **Créer un instantané immédiatement et garder cette dernière disponible pour l'initialisation des abonnements** (réplication transactionnelle)  
 Activez cette case à cocher pour créer un instantané immédiatement après la fin de l'Assistant Nouvelle publication. Désactivez cette case à cocher si vous comptez modifier les propriétés d'instantané dans la boîte de dialogue **Propriétés de la publication** avant la génération d'un instantané ou si vous lancez l'abonné sans instantané. Pour plus d’informations, consultez [Initialiser un abonnement transactionnel sans instantané](initialize-a-transactional-subscription-without-a-snapshot.md).  
  
> [!NOTE]  
>  Il se peut que l'Assistant demande une connexion au serveur de distribution pour pouvoir démarrer le travail approprié pour l'Agent de distribution ou l'Agent de fusion.  
  
 **Planifier l'exécution de l'Agent d'instantané aux heures suivantes**  
 Acceptez la planification par défaut pour l'exécution de l'Agent d'instantané ou cliquez sur **Modifier** pour en spécifier une.  
  
## <a name="see-also"></a>Voir aussi  
 [Create a Publication](publish/create-a-publication.md)   
 [Créer et appliquer l’instantané initial](create-and-apply-the-initial-snapshot.md)   
 [Afficher et modifier les propriétés d’une publication](publish/view-and-modify-publication-properties.md)   
 [Initialiser un abonnement avec un instantané](initialize-a-subscription-with-a-snapshot.md)   
 [Publier des données et des objets de base de données](publish/publish-data-and-database-objects.md)   
 [Présentation des Agents de réplication](agents/replication-agents-overview.md)  
  
  
