---
title: Modification de données (MDX) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- modifying data [MDX]
- Multidimensional Expressions [Analysis Services], data modifications
- MDX [Analysis Services], data modifications
- data modifications [MDX]
ms.assetid: 363b662c-b839-4971-bbd7-1842f73ce141
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 3a1523655490e9dad4fc42f3a0f256f39a60c21b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36042575"
---
# <a name="modifying-data-mdx"></a>Modification de données (MDX)
  Outre l’utilisation de la syntaxe MDX (Multidimensional Expressions) pour récupérer et gérer les données de dimensions et de cubes, vous pouvez utiliser MDX pour mettre à jour les données de la dimension ou du cube, ou encore pour procéder à leur *écriture différée*. Ces mises à jour peuvent être temporaires (comme pour l'analyse spéculative, du type « Que se passe-t-il si ») ou permanentes (comme lorsque des modifications doivent être apportées en fonction de l'analyse de données).  
  
 Les mises à jour de données se produisent au niveau de la dimension ou du cube :  
  
 **Écriture différée de dimensions**  
 L’instruction [ALTER CUBE Statement (MDX)](/sql/mdx/mdx-data-definition-alter-cube) permet de modifier les données d’une dimension activée en écriture, tandis que l’instruction [REFRESH CUBE Statement (MDX)](/sql/mdx/mdx-data-definition-refresh-cube) sert à illustrer les processus de suppression, création et mise à jour des valeurs d’attributs. Il est également possible d'utiliser l'instruction ALTER CUBE pour effectuer des opérations complexes, notamment la suppression de l'intégralité d'une sous-arborescence dans une hiérarchie et la promotion des enfants d'un membre supprimé.  
  
 **Écriture différée de cubes**  
 Pour effectuer des mises à jour d’un cube activé en écriture, vous devez utiliser l’instruction [UPDATE CUBE](/sql/mdx/mdx-data-manipulation-update-cube) . L’instruction UPDATE CUBE permet de mettre à jour un tuple avec une valeur spécifique. L’instruction [REFRESH CUBE (MDX)](/sql/mdx/mdx-data-definition-refresh-cube) permet d’actualiser les données d’une session client avec les données mises à jour du serveur.  
  
 Pour plus d’informations, consultez [Utilisation de l’écriture différée de cubes à l’aide de &#40;MDX&#41;](mdx-data-modification-using-cube-writebacks.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Principes de base de requête MDX &#40;Analysis Services&#41;](mdx-query-fundamentals-analysis-services.md)  
  
  
