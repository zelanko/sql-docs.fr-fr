---
title: Extension d’OLAP par des personnalisations | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Analysis Services, extensibility
ms.assetid: 348e49fc-4390-43c1-9b6c-61b386ff4373
caps.latest.revision: 9
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: d2c1bdea4c59a047f613033ae0e8aa8515c8232f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36152243"
---
# <a name="extending-olap-through-personalizations"></a>Extension d'OLAP par des personnalisations
  Microsoft [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] fournit de nombreuses fonctions intrinsèques à utiliser avec les langages MDX (Multidimensional Expressions) et DMX (Data Mining Extensions). Ces fonctions sont conçues pour accomplir toutes les opérations possibles, depuis les calculs statistiques standard jusqu'au parcours des membres d'une hiérarchie. Cependant, comme avec tout autre produit complexe et puissant, il est toujours nécessaire d'étendre les fonctionnalités de ce type d'outil.  
  
 Par conséquent, Analysis Services vous permet d'ajouter des assemblys et des extensions personnalisées à une instance du service, afin de répondre aux besoins de votre entreprise chaque fois que les fonctionnalités standard sont insuffisantes.  
  
## <a name="assemblies"></a>Assemblys  
 Les assemblys vous permettent d'étendre les fonctions d'entreprise de MDX et de DMX. Vous générez les fonctionnalités souhaitées dans une bibliothèque, telle qu'une bibliothèque de liens dynamiques (DLL), puis vous ajoutez cette bibliothèque en tant qu'assembly à une instance d'Analysis Services ou à une base de données Analysis Services. Les méthodes publiques de la bibliothèque sont alors exposées en tant que fonctions définies par l'utilisateur aux expressions, procédures, calculs, actions et applications clientes MDX et DMX.  
  
## <a name="personalized-extensions"></a>Extensions personnalisées  
 Les extensions de personnalisation SQL Server Analysis Services sont la base de l'idée d'implémentation d'une architecture de plug-in. Elles sont une modification simple et élégante de l'architecture d'assembly managée existante et sont exposées partout dans le modèle objet Analysis Services <xref:Microsoft.AnalysisServices.AdomdServer>, la syntaxe MDX (Multidimensional Expressions) et les ensembles de lignes de schéma.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des assemblys de modèle multidimensionnel](../multidimensional-model-assemblies-management.md)   
 [Extensions de personnalisation d’Analysis Services](analysis-services-personalization-extensions.md)  
  
  