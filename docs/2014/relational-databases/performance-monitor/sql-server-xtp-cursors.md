---
title: Les curseurs XTP | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 84bf4654-3ef7-4d7f-a269-c8bb4ed4acad
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b591aa8e89200ca863b1e8196c383c506401fc3e
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2018
ms.locfileid: "52759671"
---
# <a name="xtp-cursors"></a>Curseurs XTP
  L'objet de performance Curseurs XTP contient des compteurs connexes aux curseurs internes du moteur XTP. Les curseurs sont des blocs de construction de bas niveau que le moteur XTP utilise pour traiter les requêtes [!INCLUDE[tsql](../../includes/tsql-md.md)] . Par conséquent, vous ne pouvez pas les contrôler directement.  
  
 Ce tableau décrit les **curseurs XTP** compteurs.  
  
|Compteur|Description|  
|-------------|-----------------|  
|**Suppressions des curseurs par seconde**|Nombre de suppressions des curseurs (en moyenne), par seconde.|  
|**Insertions des curseurs par seconde**|Nombre d'insertions des curseurs (en moyenne), par seconde.|  
|**Analyses des curseurs démarrées par seconde**|Nombre d'analyses des curseurs démarrées (en moyenne), par seconde.|  
|**Violations de contrainte unique des curseurs par seconde**|Nombre de violations de contrainte unique (en moyenne), par seconde.|  
|**Mises à jour des curseurs par seconde**|Nombre de mises à jour des curseurs (en moyenne), par seconde.|  
|**Conflits d'écriture des curseurs par seconde**|Nombre de conflits d'écriture-écriture vers la même version de ligne (en moyenne), par seconde.|  
|**Nouvelles tentatives d'analyse d'angles inutilisés par seconde (sortie utilisateur)**|Nombre de tentatives d'analyse dues à des conflits d'écriture lors des nettoyages d'angles inutilisés indiqué par une analyse de table complète de l'utilisateur (en moyenne), par seconde. Il s'agit d'un compteur de très bas niveau, non destiné au client.|  
|**Lignes expirées supprimées par seconde**|Nombre de lignes expirées supprimées par les curseurs (en moyenne), par seconde.|  
|**Lignes expirées touchées par seconde**|Nombre de lignes expirées touchées par les curseurs (en moyenne), par seconde.|  
|**Lignes retournées par seconde**|Nombre de lignes retournées par les curseurs (en moyenne), par seconde.|  
|**Lignes touchées par seconde**|Nombre de lignes touchées par les curseurs (en moyenne), par seconde.|  
|**Lignes en cours de suppression, touchées par seconde**|Nombre de lignes expirant touchées par les curseurs (en moyenne), par seconde. Une ligne expire si la transaction qui l’a supprimée est toujours active (c’est-à-dire qu’elle n’a pas encore été validée ou annulée.)|  
  
## <a name="see-also"></a>Voir aussi  
 [XTP &#40;In-Memory OLTP&#41; les compteurs de performances](../../integration-services/performance/performance-counters.md)  
  
  
