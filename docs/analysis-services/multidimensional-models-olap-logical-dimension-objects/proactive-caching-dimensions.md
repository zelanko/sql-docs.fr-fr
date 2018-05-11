---
title: Mise en cache proactive (Dimensions) | Documents Microsoft
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3cb3631ac279ce688a10461f676638fc4863929f
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2018
---
# <a name="proactive-caching-dimensions"></a>Mise en cache proactive (dimensions)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  La mise en cache proactive fournit la création et la gestion de la mise en cache MOLAP automatique pour les objets OLAP. Les cubes incorporent immédiatement les modifications apportées aux données dans la base de données, en fonction des notifications reçues de cette dernière. L'objectif de la mise en cache proactive est de fournir la performance MOLAP traditionnelle tout en conservant la rapidité et la facilité de gestion offertes par ROLAP.  
  
 Un objet <xref:Microsoft.AnalysisServices.ProactiveCaching> simple est composé d'une spécification temporelle et d'une notification de table. La spécification temporelle définit le délai de mise à jour du cache après qu'une notification de modification a été reçue. La notification de table définit le schéma de notification entre la table de données et l'objet <xref:Microsoft.AnalysisServices.ProactiveCaching>.  
  
  
