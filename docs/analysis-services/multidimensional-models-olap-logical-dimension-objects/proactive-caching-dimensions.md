---
title: Mise en cache proactive (Dimensions) | Documents Microsoft
ms.custom: 
ms.date: 03/06/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords:
- dimensions [Analysis Services], proactive caching
- proactive caching [Analysis Services]
ms.assetid: 7d57fe93-6e5f-4a50-844f-dd2bbdbb94a5
caps.latest.revision: "8"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 70624fe00b62733079aa0ffde47f8928cae0324d
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2017
---
# <a name="proactive-caching-dimensions"></a>Mise en cache proactive (dimensions)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Mise en cache proactive fournit la création du cache MOLAP automatique et gestion pour les objets OLAP. Les cubes incorporent immédiatement les modifications apportées aux données dans la base de données, en fonction des notifications reçues de cette dernière. L'objectif de la mise en cache proactive est de fournir la performance MOLAP traditionnelle tout en conservant la rapidité et la facilité de gestion offertes par ROLAP.  
  
 Un objet <xref:Microsoft.AnalysisServices.ProactiveCaching> simple est composé d'une spécification temporelle et d'une notification de table. La spécification temporelle définit le délai de mise à jour du cache après qu'une notification de modification a été reçue. La notification de table définit le schéma de notification entre la table de données et l'objet <xref:Microsoft.AnalysisServices.ProactiveCaching>.  
  
  
