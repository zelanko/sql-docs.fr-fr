---
title: "Configurer le niveau (tous) pour les hiérarchies d’attributs | Documents Microsoft"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- All members
- IsAggregatable property
- topmost levels [Analysis Services]
- (All) levels
- AttributeAllMemberName property
- levels [Analysis Services]
- members [Analysis Services], All
- AllMemberName property
ms.assetid: 0cb35e6f-b10f-483d-b893-78f6ca3979fd
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 46870a942fad5b41d91177772175e9cad43fad0a
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="database-dimensions---configure-the-all-level-for-attribute-hierarchies"></a>Dimensions de base de données - configurer le niveau (tous) pour les hiérarchies d’attributs
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], le niveau (All) est un niveau facultatif, généré par le système. Il contient un seul membre dont la valeur est l'agrégation des valeurs de tous les membres du niveau situé juste en dessous. Ce membre est appelé membre Tous. Ce membre est créé par le système et il ne figure pas dans la table de dimension. Étant donné que le membre du niveau (Tous) se trouve au sommet d'une hiérarchie, sa valeur est l'agrégation consolidée des valeurs de tous les membres de la hiérarchie. Le membre Tous sert souvent de membre par défaut d'une hiérarchie.  
  
 La présence d’un niveau (Tous) dans une hiérarchie d’attributs dépend de la valeur de la propriété **IsAggregatable** de l’attribut, et la présence d’un niveau (Tous) dans une hiérarchie définie par l’utilisateur dépend de la propriété **IsAggregatable** de l’attribut au niveau le plus élevé de la hiérarchie définie par l’utilisateur. Si la propriété **IsAggregatable** a la valeur **True**, il existera un niveau (Tous). Au contraire, une hiérarchie n’a pas de niveau (Tous) si sa propriété **IsAggregatable** a la valeur **False**.  
  
## <a name="establishing-the-topmost-level"></a>Établissement du niveau le plus élevé  
 Si la propriété **IsAggregatable** de l’attribut source d’un niveau d’une hiérarchie a la valeur **False** , aucun niveau agrégeable ne peut apparaître dans la hiérarchie au-dessus de ce niveau. Un niveau non agrégeable doit être le niveau le plus élevé d’une hiérarchie, ou la propriété **IsAggregatable** des attributs sources des niveaux qui sont au-dessus de lui doit aussi avoir la valeur **False**.  
  
## <a name="all-member-and-all-level"></a>Membre Tous et niveau (Tous)  
 Le membre unique du niveau (Tous) est appelé membre Tous. La propriété **AttributeAllMemberName**d’une dimension spécifie le nom du membre Tous pour les attributs d’une dimension. La propriété **AllMemberName** d’une hiérarchie spécifie le nom du membre Tous de cette hiérarchie.  
  
## <a name="see-also"></a>Voir aussi  
 [Définir un membre par défaut](../../analysis-services/multidimensional-models/attribute-properties-define-a-default-member.md)  
  
  
