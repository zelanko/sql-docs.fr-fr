---
title: Configurer le niveau (tous) pour les hiérarchies d’attributs | Documents Microsoft
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
- All members
- IsAggregatable property
- topmost levels [Analysis Services]
- (All) levels
- AttributeAllMemberName property
- levels [Analysis Services]
- members [Analysis Services], All
- AllMemberName property
ms.assetid: 0cb35e6f-b10f-483d-b893-78f6ca3979fd
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: e61b7606ab4a7c2418294133ad7c4f3b03672df1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36153813"
---
# <a name="configure-the-all-level-for-attribute-hierarchies"></a>Configurer le niveau (Tous) des hiérarchies d'attributs
  Dans [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], le niveau (Tous) est un niveau facultatif, généré par le système. Il contient un seul membre dont la valeur est l'agrégation des valeurs de tous les membres du niveau situé juste en dessous. Ce membre est appelé membre Tous. Ce membre est créé par le système et il ne figure pas dans la table de dimension. Étant donné que le membre du niveau (Tous) se trouve au sommet d'une hiérarchie, sa valeur est l'agrégation consolidée des valeurs de tous les membres de la hiérarchie. Le membre Tous sert souvent de membre par défaut d'une hiérarchie.  
  
 Dépend de la présence d’un niveau (tous) dans une hiérarchie d’attribut du `IsAggregatable` dépend de la définition de propriété pour l’attribut et la présence d’un niveau (tous) dans une hiérarchie définie par l’utilisateur le `IsAggregatable` propriété de l’attribut au niveau supérieur de hiérarchie définie par l’utilisateur. Si la propriété `IsAggregatable` a la valeur `True`, il existera un niveau (Tous). Au contraire, une hiérarchie n'a pas de niveau (Tous) si sa propriété `IsAggregatable` a la valeur `False`.  
  
## <a name="establishing-the-topmost-level"></a>Établissement du niveau le plus élevé  
 Si la propriété `IsAggregatable` de l'attribut source d'un niveau d'une hiérarchie a la valeur `False`, aucun niveau agrégeable ne peut apparaître dans la hiérarchie au-dessus de ce niveau. Un niveau non agrégeable doit être le niveau le plus élevé d'une hiérarchie, ou la propriété `IsAggregatable` des attributs sources des niveaux qui sont au-dessus de lui doit aussi avoir la valeur `False`.  
  
## <a name="all-member-and-all-level"></a>Membre Tous et niveau (Tous)  
 Le membre unique du niveau (Tous) est appelé membre Tous. Le `AttributeAllMemberName`propriété sur une dimension Spécifie le nom du membre tous pour les attributs dans une dimension. La propriété `AllMemberName` d'une hiérarchie spécifie le nom du membre Tous de cette hiérarchie.  
  
## <a name="see-also"></a>Voir aussi  
 [Définir un membre par défaut](attribute-properties-define-a-default-member.md)  
  
  