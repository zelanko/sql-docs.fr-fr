---
title: Garbage Collection XTP | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 64ae91e5-b420-44b4-af1a-f8bca83d7f41
caps.latest.revision: 5
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: c2a968f1fa15f0f61d988f5068ab5ce39be0808e
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37299931"
---
# <a name="xtp-garbage-collection"></a>Garbage collection XTP
  L'objet de performance Garbage collection XTP contient les compteurs connexes au garbage collector du moteur XTP.  
  
 Ce tableau décrit les compteurs **Garbage collection XTP** .  
  
|Compteur|Description|  
|-------------|-----------------|  
|**Nouvelles tentatives d'analyse d'angles inutilisés par seconde (sortie GC)**|Nombre de tentatives d'analyse dues à des conflits d'écriture lors des nettoyages d'angles inutilisés indiqué par le garbage collector (en moyenne), par seconde. Il s'agit d'un compteur de très bas niveau, non destiné au client.|  
|**Éléments de travail de GC principal par seconde**|Nombre d'éléments de travail traités par le thread GC principal.|  
|**Élément de travail de GC parallèle par seconde**|Nombre de fois qu'un thread parallèle a exécuté un élément de travail GC.|  
|**Lignes traitées par seconde**|Nombre de lignes traitées par le garbage collector (en moyenne), par seconde.|  
|**Lignes traitées par seconde (d'abord dans le compartiment, puis supprimées)**|Nombre de lignes traitées par le garbage collector qui étaient initialement dans le compartiment de hachage correspondant, et qui ont pu ensuite être supprimées immédiatement (en moyenne), par seconde.|  
|**Lignes traitées par seconde (d'abord dans le compartiment)**|Nombre de lignes traitées par le garbage collector qui étaient initialement dans le compartiment de hachage correspondant (en moyenne), par seconde.|  
|**Lignes traitées par seconde (marquées pour la dissociation)**|Nombre de lignes traitées par le garbage collector qui étaient déjà marquées pour la dissociation (en moyenne), par seconde.|  
|**Lignes traitées par seconde (pas de nettoyage requis)**|Nombre de lignes traitées par le garbage collector qui ne nécessitent pas de nettoyage d'angle inutilisé (en moyenne), par seconde.|  
|**Lignes expirées lors des nettoyages, supprimées par seconde**|Nombre de lignes expirées supprimées lors des nettoyages d'angles inutilisés (en moyenne), par seconde.|  
|**Lignes expirées lors des nettoyages, touchées par seconde**|Nombre de lignes expirées touchées lors des nettoyages d'angles inutilisés (en moyenne), par seconde.|  
|**Lignes expirant touchées lors des nettoyages, par seconde**|Nombre de lignes expirant touchées lors des nettoyages d'angles inutilisés (en moyenne), par seconde.|  
|**Lignes touchées lors des nettoyages, par seconde**|Nombre de lignes touchées lors des nettoyages d'angles inutilisés (en moyenne), par seconde.|  
|**Analyses de nettoyage démarrées par seconde**|Nombre d'analyses de nettoyage d'angles inutilisés démarrées (en moyenne), par seconde.|  
  
## <a name="see-also"></a>Voir aussi  
 [XTP &#40;In-Memory OLTP&#41; les compteurs de performances](../../integration-services/performance/performance-counters.md)  
  
  
