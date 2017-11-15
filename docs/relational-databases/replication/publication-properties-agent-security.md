---
title: "Propriétés de la publication, page Sécurité de l’agent | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.rep.newpubwizard.pubproperties.agentsecurity.f1
ms.assetid: 03945aac-66f2-4370-b5d1-c1de694bc4c1
caps.latest.revision: "21"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2866488497c4b5e1e00200e5e3fc87547e161d0c
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="publication-properties-agent-security"></a>Propriétés de la publication, page Sécurité de l'agent
  La page **Sécurité de l'agent** de la boîte de dialogue **Propriétés de la publication** vous permet d'accéder aux paramètres des comptes sous lesquels s'exécutent les agents ci-après. Elle vous permet également d'établir des connexions aux ordinateurs dans une topologie de réplication :  
  
-   Agent d'instantané pour toutes les publications ;  
  
-   Agent de lecture du journal pour toutes les publications transactionnelles ; Il existe un Agent de lecture du journal pour chaque base de données publiée en vue de la réplication transactionnelle. La modification des paramètres de l'Agent de lecture du journal affecte toutes les publications transactionnelles dans une base de données.  
  
-   l'Agent de lecture de la file d'attente propre aux publications transactionnelles autorisant les abonnements de mise à jour dans la file d'attente ; Il existe un Agent de lecture de la file d'attente pour chaque base de données de distribution. La modification des paramètres de l'Agent de lecture de la file d'attente affecte toutes les publications transactionnelles avec des abonnements mis à jour en attente qui utilisent la même base de données de distribution. Pour plus d’informations sur les paramètres de sécurité de l’Agent de lecture de la file d’attente, consultez [Afficher et modifier les paramètres de sécurité de la réplication](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md).  
  
 Pour plus d'informations sur les paramètres de sécurité et les autorisations requis par chaque agent, consultez [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
## <a name="options"></a>Options  
 **Paramètres de sécurité** ou **Créer un Agent**  
 Si un travail d'agent a été créé, cliquez sur **Paramètres de sécurité** pour accéder à une boîte de dialogue qui vous permet de modifier les paramètres de sécurité d'un agent. Dans le cas contraire, cliquez sur **Créer un Agent** pour en créer un et spécifier les paramètres de sécurité.  
  
## <a name="see-also"></a>Voir aussi  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Afficher et modifier les propriétés d’une publication](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Publier des données et des objets de base de données](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   
 [Bonnes pratiques en matière de sécurité de la réplication](../../relational-databases/replication/security/replication-security-best-practices.md)   
 [Sécurité et protection &#40;réplication&#41;](../../relational-databases/replication/security/security-and-protection-replication.md)  
  
  
