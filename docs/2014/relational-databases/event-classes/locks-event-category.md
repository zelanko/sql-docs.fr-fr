---
title: Verrous, catégorie d’événement | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
topic_type:
- apiref
helpviewer_keywords:
- Locks event category [SQL Server]
- SQL Server event classes, Locks event category
- event classes [SQL Server], Locks event category
- lock escalation [SQL Server], locks event category
ms.assetid: 27d6afa2-7dab-4fe7-a1ad-064b879dc654
caps.latest.revision: 26
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c44a8bd63dca681f303e435c60a5f23aff37e36d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36143901"
---
# <a name="locks-event-category"></a>Verrous, catégorie d’événement
  Utilisez les classes d’événements de la catégorie d’événements **Locks** pour surveiller l’activité de verrouillage dans une instance du [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]. Ces classes d'événements facilitent la recherche de problèmes de verrouillage dus au fait que plusieurs utilisateurs lisent et modifient simultanément des données.  
  
 Du fait que le [!INCLUDE[ssDE](../../includes/ssde-md.md)] traite souvent de nombreux verrous, la capture des classes d’événements **Locks** peut générer une surcharge importante sur le processeur et créer des tables ou des fichiers de trace volumineux.  
  
## <a name="in-this-section"></a>Dans cette section  
  
|Rubrique|Description|  
|-----------|-----------------|  
|[Classe d'événements Deadlock Graph](deadlock-graph-event-class.md)|Fournit une description XML d'un blocage.|  
|[Classe d'événements Lock:Acquired](lock-acquired-event-class.md)|Indique qu'un verrou a été acquis sur une ressource, par exemple une ligne d'une table.|  
|[Classe d'événements Lock:Cancel](lock-cancel-event-class.md)|Trace les requêtes de verrous qui ont été annulées avant l'acquisition du verrou (par exemple pour empêcher un blocage).|  
|[Classe d'événements Lock:Deadlock Chain](lock-deadlock-chain-event-class.md)|Contrôle les conditions de blocage et les objets impliqués.|  
|[Classe d'événements Lock:Deadlock](lock-deadlock-event-class.md)|Trace à quel moment une transaction a demandé un verrou sur une ressource déjà verrouillée par une autre transaction, ce qui provoque un blocage.|  
|[Classe d'événements Lock:Escalation](lock-escalation-event-class.md)|Indique qu'un verrouillage spécifique s'est transformé en verrouillage de plus grande ampleur.|  
|[Lock:Released, classe d’événements](lock-released-event-class.md)|Trace la libération d'un verrou.|  
|[Lock:Timeout &#40;timeout &#62; 0&#41;, classe d’événements](lock-timeout-timeout-0-event-class.md)|Trace à quel moment les demandes de verrous ne sont pas possibles car une autre transaction possède un verrou de blocage sur la ressource demandée. Cet événement se produit uniquement lorsque la valeur d'expiration du verrou est supérieure à zéro (0).|  
|[Classe d'événements Lock:Timeout](lock-timeout-event-class.md)|Trace à quel moment les demandes de verrous ne sont pas possibles car une autre transaction possède un verrou de blocage sur la ressource demandée.|  
  
  