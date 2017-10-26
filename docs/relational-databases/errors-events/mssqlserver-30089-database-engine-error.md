---
title: MSSQLSERVER_30089 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords:
- 9992 (Database Engine error)
ms.assetid: 188e5bde-6865-4740-a2b2-582be8f55c77
caps.latest.revision: 17
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: c42bbbb05ba2cb78628433815effb5ef7ce48132
ms.contentlocale: fr-fr
ms.lasthandoff: 06/22/2017

---
# <a name="mssqlserver30089"></a>MSSQLSERVER_30089
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|30089|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|IFTS_FDHOST_TERMINATEDABNORMAL|  
|Texte du message|Le processus hôte de démon de filtre de texte intégral (FDHost) s'est arrêté anormalement. Cela peut se produire si un composant linguistique, tel qu'un analyseur lexical, un générateur de formes dérivées ou un filtre configuré de façon incorrecte ou présentant un dysfonctionnement a provoqué une erreur irrécupérable pendant l'indexation de texte intégral ou le traitement de requête. Le processus sera redémarré automatiquement.|  
  
## <a name="explanation"></a>Explication  
Le processus hôte de démon de filtre de texte intégral a rencontré un problème qui l'a forcé à s'arrêter anormalement. La cause du problème peut être un document mis en forme de manière incorrecte, un bogue dans le filtre ou l'analyseur lexical, ou un problème dans le démon de filtre.  
  
## <a name="user-action"></a>Action de l'utilisateur  
En règle générale, le démon corrige l'erreur. Si le problème persiste, une résolution définitive s'avère nécessaire. Pour isoler le problème, essayez les opérations suivantes :  
  
1.  Si un nouveau composant linguistique a été installé récemment, supprimez-le du système.  
  
2.  Examinez le journal d'analyse pour identifier les nouveaux documents qui n'ont pas pu faire l'objet d'une indexation de texte intégral, puis supprimez-les.  
  
## <a name="see-also"></a>Voir aussi  
[sp_help_fulltext_system_components &#40;Transact-SQL&#41;](~/relational-databases/system-stored-procedures/sp-help-fulltext-system-components-transact-sql.md)  
[Configurer et gérer les analyseurs lexicaux et générateurs de formes dérivées pour la recherche](~/relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)  
[Configurer et gérer des filtres pour la recherche](~/relational-databases/search/configure-and-manage-filters-for-search.md)  
  

