---
title: "Modification de donn&#233;es (MDX) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modification de données (MDX)"
  - "Expressions multidimensionnelles [Analysis Services], modifications de données"
  - "MDX [Analysis Services], modifications de données"
  - "modification de données [MDX]"
ms.assetid: 363b662c-b839-4971-bbd7-1842f73ce141
caps.latest.revision: 30
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# Modification de donn&#233;es (MDX)
  Outre l’utilisation de la syntaxe MDX (Multidimensional Expressions) pour récupérer et gérer les données de dimensions et de cubes, vous pouvez utiliser MDX pour mettre à jour les données de la dimension ou du cube, ou encore pour procéder à leur *écriture différée*. Ces mises à jour peuvent être temporaires (comme pour l'analyse spéculative, du type « Que se passe-t-il si ») ou permanentes (comme lorsque des modifications doivent être apportées en fonction de l'analyse de données).  
  
 Les mises à jour de données se produisent au niveau de la dimension ou du cube :  
  
 **Écriture différée de dimensions**  
 L’instruction [ALTER CUBE Statement (MDX)](../Topic/ALTER%20CUBE%20Statement%20\(MDX\).md) permet de modifier les données d’une dimension activée en écriture, tandis que l’instruction [REFRESH CUBE Statement (MDX)](../Topic/REFRESH%20CUBE%20Statement%20\(MDX\).md) sert à illustrer les processus de suppression, création et mise à jour des valeurs d’attributs. Il est également possible d'utiliser l'instruction ALTER CUBE pour effectuer des opérations complexes, notamment la suppression de l'intégralité d'une sous-arborescence dans une hiérarchie et la promotion des enfants d'un membre supprimé.  
  
 **Écriture différée de cubes**  
 Pour effectuer des mises à jour d’un cube activé en écriture, vous devez utiliser l’instruction [UPDATE CUBE](../Topic/UPDATE%20CUBE%20Statement%20\(MDX\).md). L’instruction UPDATE CUBE permet de mettre à jour un tuple avec une valeur spécifique. L’instruction [REFRESH CUBE (MDX)](../Topic/REFRESH%20CUBE%20Statement%20\(MDX\).md) permet d’actualiser les données d’une session client avec les données mises à jour du serveur.  
  
 Pour plus d’informations, consultez [Utilisation de l’écriture différée de cubes à l’aide de &#40;MDX&#41;](../../../analysis-services/multidimensional-models/mdx/using-cube-writebacks-mdx.md).  
  
## Voir aussi  
 [Principes de base des requêtes MDX &#40;Analysis Services&#41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)  
  
  